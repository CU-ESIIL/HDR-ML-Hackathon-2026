# Quick start for working with GoCommands

Example path to an output folder from a runner job on VICE App, using the terminal
```bash
ls ~/data-store/home/esokol/ESIIL_hackathon_testing/20251204_1619_runner/
```
This is what the path to the file looks like:
```bash
my_path_to_weights=~/data-store/home/esokol/ESIIL_hackathon_testing/20251204_1619_runner/model_2025-12-05_03-04-15.pth
```
To use with GoCommands, you need to format the path differently:
```bash
# modify the path to work with gocmd
# i.e., replace "~/data-store" with "/iplant/home"
my_gocmd_path_to_weights=/iplant/home/esokol/ESIIL_hackathon_testing/20251204_1619_runner/model_2025-12-05_03-04-15.pth
```

Then, use GoCommands to copy file to a local directory on your VICE app. It is recommended to use GoCommands to move large files, then zip them "locally", then move them back to persistent storage using GoCommands. 

```bash
# initialize gocmd (only need to do once per terminal session)
gocmd init
```
```bash
# check that gocmd is working
gocmd env
```
```bash
# copy the file to the VM
gocmd get --progress "$my_gocmd_path_to_weights" ./
```
Create a zip archive to submit to Codabench. You can do this using the `scripts/make_submission_zip.sh` script
```bash
./make_submission_zip.sh
```

Move the zipped file back to your datastore:
```bash
# Set the output path
my_gocmd_write_path=/iplant/home/esokol/ESIIL_hackathon_testing/zip_submission.zip

# Transfer the file
gocmd put --progress zip_submission.zip "$my_gocmd_write_path"
```