# Quick start guide HDR ML Hackathon 2026
This document provides the basic steps to:
1. Get started using the CyVerse Discovery Environment (DE)
2. Train a baseline model for the Beetles as Sentinel Taxa theme for the challenge, but these steps should also work for the other challenge themes. 
3. Create a submission for the ML challenge with the proper formatting
4. Upload your submission for scoring via the Codabench platform

## 1. Fire up your cloud compute on CyVerse

### 1.1. Starting your cloud compute
- Go to https://de.cyverse.org
- Find the VICE app at
https://de.cyverse.org/apps/de/165baf1e-be83-11f0-bf87-008cfa5ae621/launch
    - This app provides cloud compute with access to a GPU and persistent storage in the CyVerse Data Store
    - Find detailed instructions using the Beetle example here: https://github.com/jeffgillan/HDR-SMood-Challenge-sample

### 1.2. Setting up your own branch of the GitHub repo to access **MORE COMPUTE POWER**  
- **FOR MORE COMPUTE POWER**: How to use a **runner** to send compute to JS2 here: https://github.com/jeffgillan/HDR-SMood-Challenge-sample/tree/main/.github/workflows#readme
- **NOTE**: When using the runner, be sure to share write access to your designated output location in the CyVerse datastore with Jeff's account (jkentg)
- Create a branch of this repo (jeffgillan/HDR-SMood-Challenge-sample) - name it your group name or your user name

### 1.3. Configuring your Jupyter Lab 
- In the VICE app, open the terminal and type
```bash
gh auth login`
```
- Follow the prompts so you are logged in and can push to GitHub
- Clone your branch from github
```bash
git clone --branch <branch-name> https://github.com/jeffgillan/HDR-SMood-Challenge-sample.git
```

## 2. Train your model

### 2.1. Option 1 (slower): Use the compute in your CyVerse instance:
- For a detailed description of the model training code and flags/parameters, see the README at https://github.com/jeffgillan/HDR-SMood-Challenge-sample
- Open the terminal
```bash
# open terminal and load dependencies
uv sync
```
```bash
# train model - in terminal (~30-60mins)
uv run python baselines/training/BioClip2/train.py --batch_size 128 --num_workers 16 --epochs 50 --lr 2e-4
```


### 2.2. Option 2 (faster): Use a "runner" to send a job to the more powerful Jetstream2 cloud compute using GitHub actions
- Detailed instructions are here: https://github.com/jeffgillan/HDR-SMood-Challenge-sample/tree/main/.github/workflows
- To use the *runner* you must trigger GitHub actions by editing the training config json file and pushing the edited file to your branch: e.g.: 
- The filepath in the repo is `HDR-SMood-Challenge-sample/training_config.json`
```json 
{
  "script_path": "baselines/training/BioClip2/train.py",
  "epochs": 2,
  "batch_size": 128,
  "num_workers": 16,
  "cyverse_output_path": "/iplant/home/esokol/ESIIL_hackathon_testing/20251204_1424_runner/"
}
```
- commit and push your edit to your branch

NOTES: 
- Make a subfolder for each runner to write into so you can distinghish which run is which  
- Name your commits so that it's easy to identify in the github actions queue, e.g., `sokole runner 1`
- You can edit the config file on github for your branch using the GitHub web UI

## 3. Create your submission
- Your submission must be a zipped archive with the following files:
    - `requirements.txt`
    - `model.py`
    - `model.pth`
- When zipping, use the flag `-v` to monitor progress, flag `j` to strip the path and just use filenames in the zip archive, e.g.,

```bash
zip -vj \
    test_submit_bioclip2_20251201.zip \
    baselines/submissions/BioClip2/requirements.txt \
    baselines/submissions/BioClip2/model.py \
    baselines/training/BioClip2/model.pth
```
- Check your zip archive to make sure its contents are correct
```bash
zipinfo test_submit_bioclip2_20251201.zip
```
- Use GoCommands to move the submission file to the data store
```bash
gocmd init 
    # follow prompts to log in
```
```bash
gocmd put --progress test_submit_bioclip2_20251201.zip /iplant/home/esokol/ESIIL_hackathon_testing/
```
## 4. Submit to Codabench
### 4.1 (Optional) spin up Ubuntu 20.04 Desktop VICE app
- https://de.cyverse.org/apps/de/24755010-5502-11ee-9003-008cfa5ae621/launch

- Then open chrome and proceed...

### 4.2 submit using the webform
- Go to codabench site and log in at https://www.codabench.org/competitions/9854
- Go to "My Submissions" tab
- Attach and upload submission
- Submission score will appear below after it has finished running
