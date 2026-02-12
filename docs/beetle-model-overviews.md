# Model Overview: Baseline Approaches

This document provides a description of the baseline models for the Beetles theme for the 2026 HDR ML Challenge found in the GitHub repo at this link:
https://github.com/Imageomics/HDR-SMood-Challenge-sample

This document provides a summary of the four baseline modeling approaches for the HDR Scientific Mood Challenge. The challenge focuses on predicting SPEI drought indicators (30-day, 1-year, and 2-year) from beetle images, addressing out-of-distribution (OOD) generalization across different geographic and temporal domains.

## Challenge Context

The models predict three SPEI (Standardized Precipitation Evapotranspiration Index) values representing drought conditions at different timescales. All models are evaluated using R² scores for each timeframe.

---

## 1. BioClip2 (Basic Frozen Encoder)

**Location**: [`baselines/training/BioClip2/model.py`](baselines/training/BioClip2/model.py)

### Architecture
- **BioClipv2 vision encoder** (completely frozen) + 4-layer MLP regression head
- Extracts 768-dimensional features from the frozen BioClip2 encoder
- Regression head architecture: 768 → 512 → 128 → 32 → 3 (SPEI values)
- Uses GELU activations between layers

### Training Strategy
- Only trains the regression head parameters
- Frozen encoder acts as a fixed feature extractor
- Optimizer: Adam with learning rate 1e-4 (default)
- Loss: MSE on SPEI predictions

### Characteristics
- **Most lightweight**: Minimal trainable parameters
- **Fastest training**: No backpropagation through encoder
- **Baseline approach**: Relies entirely on pretrained biological knowledge
- **Best for**: Quick prototyping, when pretrained features are sufficient

---

## 2. BioClip2-ft (Fine-Tuned)

**Location**: [`baselines/training/BioClip2-ft/model.py`](baselines/training/BioClip2-ft/model.py)

### Architecture
- **Partially fine-tuned BioClip2** encoder + regression head
- Same regression head structure as basic BioClip2
- Unfreezes last N transformer blocks (default: 2) of the vision encoder
- Also trains the layer normalization layer post-encoder

### Training Strategy
- Two-stage forward pass:
  1. Frozen layers (embedding + first transformer blocks)
  2. Unfrozen layers (last N blocks + layer norm + projection)
- **Differential learning rates**:
  - Encoder blocks: lr × 0.01 (10x slower)
  - Regression head: lr (default 1e-4)
- Optimizer: Adam with separate parameter groups

### Key Methods
- `get_trainable_parameters()`: Returns parameter groups with different learning rates
- `forward_frozen()`: Processes through frozen portions
- `forward_unfrozen()`: Processes through trainable portions
- `save_parameters()` / `load_parameters()`: Custom saving for partial weights

### Characteristics
- **Adaptive**: Fine-tunes encoder to domain-specific beetle features
- **Moderate complexity**: More parameters than basic, fewer than full fine-tuning
- **Better generalization**: Can adapt high-level features while preserving low-level vision
- **Best for**: When pretrained features need task-specific adaptation

---

## 3. BioClip2-ft-did (Fine-Tuned with Domain IDs)

**Location**: [`baselines/training/BioClip2-ft-did/model.py`](baselines/training/BioClip2-ft-did/model.py)

### Architecture
- **Fine-tuned BioClip2** (same as BioClip2-ft) + **domain embedding module** + regression head
- Domain ID feature extractor:
  - Embedding layer (768-dim) for known domain IDs + padding for unknown
  - 2-layer MLP: 768 → 768 → 768
  - Layer normalization
- Final features: image features + domain ID features (element-wise addition)

### Domain Handling
- **Known domain IDs**: [32, 1, 99, 4, 3, 7, 9, 202, 11, 46] (10 training domains)
- **Unknown domains**: Mapped to padding index (no learned features added)
- **Domain ID augmentation**: Randomly masks domain IDs during training with probability `domain_id_aug_prob`

### Training Strategy
- Same differential learning rates as BioClip2-ft
- Domain augmentation helps prevent overfitting to domain-specific patterns
- Supports inference with or without domain IDs

### Key Methods
- `forward_unfrozen(x, domain_ids)`: Accepts optional domain IDs
- Handles missing or unknown domain IDs gracefully via padding

### Characteristics
- **Explicitly models domain shift**: Learns domain-specific adjustments
- **Flexible**: Works with or without domain information at test time
- **Most complex**: Largest number of trainable parameters
- **Best for**: When domain information is available and distribution shift is significant

---

## 4. Dino2 (Self-Supervised Vision Transformer)

**Location**: [`baselines/training/Dino2/model.py`](baselines/training/Dino2/model.py)

### Architecture
- **DinoV2 encoder** (frozen) + **spatial convolution module** + regression head
- Extracts patch tokens (256 tokens × 768-dim) from DINOv2
- Preserves spatial structure by reshaping to 16×16 grid
- Spatial processing:
  - Conv2d: 768×16×16 → 768×12×12 (kernel=5, padding=0)
  - ReLU activation
  - Conv2d: 768×12×12 → 1024×1×1 (kernel=12, padding=0)
  - ReLU activation
- Regression head: 1024 → 512 → 128 → 32 → 3 (with GELU)

### Training Strategy
- Only trains the spatial convolution module and regression head
- DINOv2 encoder remains frozen
- Optimizer: Adam with learning rate on regression parameters only

### Characteristics
- **Spatial reasoning**: Explicitly preserves and processes spatial relationships in patch tokens
- **General-purpose vision**: Uses self-supervised features not specialized for biology
- **Alternative foundation**: Different from domain-specific BioClip2
- **Best for**: When spatial patterns are important, or as a non-biology-specific baseline

---

## Comparison Summary

| Model | Encoder | Fine-tuning | Domain Info | Spatial Processing | Complexity |
|-------|---------|-------------|-------------|-------------------|------------|
| **BioClip2** | BioClipv2 | None (frozen) | No | Pooled features | Lowest |
| **BioClip2-ft** | BioClipv2 | Last 2 blocks | No | Pooled features | Moderate |
| **BioClip2-ft-did** | BioClipv2 | Last 2 blocks | Yes (embeddings) | Pooled features | Highest |
| **Dino2** | DinoV2 | None (frozen) | No | CNN on spatial grid | Moderate |

## Training Characteristics

All models:
- Predict 3 SPEI values (30-day, 1-year, 2-year drought indicators)
- Use MSE loss for training
- Evaluate using R² scores per timeframe
- Support batch processing with GPU acceleration
- Load data from [Hugging Face Sentinel Beetles Dataset](https://huggingface.co/datasets/imageomics/sentinel-beetles)

## When to Use Each Model

- **BioClip2**: Fastest baseline, good starting point, limited by frozen features
- **BioClip2-ft**: When you need better task adaptation without external information
- **BioClip2-ft-did**: When domain labels are available and domain shift is a primary concern
- **Dino2**: When you want a non-biology-specific alternative or suspect spatial patterns are important

## References

- **BioCLIPv2**: Gu, Jianyang, et al. "Bioclip 2: Emergent properties from scaling hierarchical contrastive learning." arXiv preprint arXiv:2505.23883 (2025).
- **DINOv2**: Oquab, Maxime, et al. "Dinov2: Learning robust visual features without supervision." arXiv preprint arXiv:2304.07193 (2023).

