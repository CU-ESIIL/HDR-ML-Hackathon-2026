# HDR-ML-Hackathon-Virtual-2026
This repo documents resources for the HDR ML Hackathon 2026 event at CU Boulder

[REGISTER HERE](https://docs.google.com/forms/d/e/1FAIpQLSfGlUkZMItr1x7SWwGJarW6vYcFIGg4gP0J_rgK8ODo3PB7ig/viewform)
<br>
<br>
**Learn more about the NSF HDR ML Challenge [here](https://www.nsfhdr.org/mlchallenge-y2) and prize info [here](https://www.codabench.org/competitions/9854/#:~:text=Prize%20Pool%20for%20HDR%20ML%20Challenges%202nd%20year).**

## Pre-event virtual bootcamp (OPTIONAL)
* Tuesday, Feb 10, 2026 10-1200 MST
* Register (link above) for zoom link

## Event Info
* **When**: Thursday, Feb 12, 1000-1400 MST  
* **Where**: Virtual, register (above) for Zoom link
<br>

This event is being organized by:  
* The [National Ecological Observatory Network (NEON), Battelle](https://www.neonscience.org/)
* The [Environmental Data Science Innovation & Impact Lab (ESIIL), CU Boulder](https://esiil.org/)
* The [Imageomics Institute](https://imageomics.org/)
* [CyVerse, University of Arizona](https://cyverse.org/)
<br>

## Agenda
* 0950-1000 - Log on, make sure audio works
* 1000-1020 - Welcome from organizers, [NEON](https://neonscience.org), and [ESIIL](https://esiil.org/)
* 1020-1040 - Introductions and Ice breaker
* 1040-1110 - Overview of [challenge themes](https://hdr-ecosystem.github.io/y2-challenge-webpage/index.html) - [SLIDES](https://docs.google.com/presentation/d/1LvYtA6iNLyXfHB2JPphATIx5avAtXYJR_M4GzkbgSC0/edit?usp=sharing)
    * Imageomics - Beetles as sentinel taxa
    * A3D3 - Neurobiology
    * iHarp - Predicting coastal flooding
* 1115-1130 - Getting started with compute resources
    * [CyVerse DE](https://de.cyverse.org) overview
* 1130-1200 - How to create a submission
    * Overview of Codabench pages
        * Beetles as Sentinel Taxa (Imageomics): https://www.codabench.org/competitions/9854/
        * Predicting Coastal Flooding (iHARP): https://www.codabench.org/competitions/10801/
        * Neural Forecasting (A3D3): https://www.codabench.org/competitions/9806/
    * Overview of baseline models/submissions
    * How to submit - Imageomics submission example
* 1200-1215 - Break!
* 1215-1245 - Breakout discussions by theme over lunch
   * Round 1 - 10 min discussion by theme (3 rooms, random assign)
   * Round 2 - 10 min discussion by theme (3 rooms, random assign)
   * Round 3 - 10 min discussion by theme (3 rooms, random assign)
* 1245-1300 - Regroup, summarize discussions
* 1300-1345 - Breakout by theme (3 rooms, self select) Folks have the option to choose smaller breakouts during this time if they form a team 
* 1345-1400 - Report outs and wrap up.

<br>
<br>

## Getting started with baseline models/code
* [Challenge 1: Beetles as Sentinel Taxa](https://github.com/jeffgillan/HDR-SMood-Challenge-sample)
* [Challenge 2: Predicting Coastal Flooding](https://github.com/iharp-institute/iHARP-ML-Challenge-2)
* [Challenge 3: Neural Forecasting](https://www.codabench.org/competitions/9806/) (NOTE: no GitHub repo, the link goes to the codabench page, see the "Starting Kit and Sample Submission" tab there for example code)
<br>
<br>
<br>
<br>
<br>

## Computing Infrastructure
<a href="https://user.cyverse.org/">
  <img src="https://github.com/ua-datalab/Geospatial_Workshops/blob/main/images/cyverse_float.gif" width="200">
</a>

<br>
<br>

Housed at the University of Arizona, CyVerse is a one-of-a-kind cloud computing system for the academic and research communities. It's mission is to design, deploy and expand a national cyberinfrastructure for scientific research and to train scientists how to use it.

* [Sign Up for Cyverse](https://user.cyverse.org/)

* [Regular Login](https://de.cyverse.org/)

* [CyVerse Learning Materials](https://learning.cyverse.org)

<br>
<br>

### Data Storage
<a href="https://cyverse.org/data-store">
  <img src="https://github.com/ua-datalab/Geospatial_Workshops/blob/main/images/data_store.png" width="150">
</a>

Cyverse Data Store is the ideal cloud storage to host your large datasets, share data with colleagues, and meet publication/grant archival requirements.  

* Pro account has a 3TB limit
* Data I/O is accessible through website GUI and command line tools such as [gocommands](https://learning.cyverse.org/ds/gocommands/)
* Share your data with your colleagues and world with a URL
* Data can be public/private, shared with anyone, set permission levels

### Sharing Folders
<img width="464" height="405" alt="Screenshot 2025-12-03 at 8 26 32 AM" src="https://github.com/user-attachments/assets/a241c32d-4104-4907-a3c2-77a5679a4c5c" />

<img width="405" height="167" alt="Screenshot 2025-12-03 at 8 28 44 AM" src="https://github.com/user-attachments/assets/58b542bd-65b3-4aad-a8c6-d47f37ba0938" />

<br>

### Shared persistent storage for this hackathon:
- Path (e.g., for GoCommands): `/iplant/home/shared/esiil/HDR_ML_challenge_2025`
- URL: https://de.cyverse.org/data/ds/iplant/home/shared/esiil/HDR_ML_challenge_2025?type=folder&resourceId=f506b3ce-b8db-11f0-b119-90e2ba675364 

<br>

### Apps Tab

Cyverse Apps are containerized software applications that include Jupyter Notebooks, Rstudio, Cloud Shell, QGIS, and VScode. These can be launched from the 'Apps' tab. When launching the apps, you can choose the size of the computing resouces you want to use (CPUs, RAM, Disk storage). 

Launching [ESIIL ML Challenge 2025](https://de.cyverse.org/apps/de/165baf1e-be83-11f0-bf87-008cfa5ae621)

Apps are ephemeral. Once they are shutdown, they disappear forever along with any data or code you have on it. Make sure to move any important data over to your personal datastore. 


<br>

### Analysis Tab

The 'Analysis' Tab is a dashboard showing the all the running and past app launches. Here you can see how much time is remaining on the app. If you need more time, you can extend the time. 

If you are finished with the app, please shut it down!! Closing browser tabs will not shutdown an app. 

<br>

### Cloud Reproducible Triangle

* Compute = your scratch pad: fast but disposable
  
* GitHub = your lab notebook: versioned, accountable, and collaborative
  
* Data Store = your filing cabinet: heavy, permanent, and backed up
  
<img width="385" height="311" alt="Screenshot 2025-12-09 at 1 58 09 PM" src="https://github.com/user-attachments/assets/06672706-4fd9-47e3-9be5-4344ec8fbd40" />

<br>

### App Command line navigation

When you first launch a Cyverse App, you are likely to be located in the directory `/home/jovyan/data-store`. This is a good place to have your workspace. You should clone repos here, bring data here, or put any folder or file here you are working with. However, anything you want to save SHOULD NOT BE STORED HERE! For permanent storage, put items in your personal datastore directory `/home/jovyan/data-store/home/<cyverse-user-name>`.

If you want to move data from workspace to permanent storage, you could type: `cp file.txt ~/data-store/home/jgillan`. Or you can copy and paste using the graphical file explorer. 

<br>
<br>

### Authenticate with Github in App
Authenticating with Github allows you to push changes back up to a repository. 

In the terminal of jupyterlab, authenticate to github by typing:

`gh auth login` 

Follow the prompts to connect the DE app with your Github account

<br>
<br>

### Clone repository to App

Best practices would be to clone git repositories to the directory `~/data-store` within the Cyverse App.

Clone using the Terminal:

`git clone --branch <branch-name> https://github.com/jeffgillan/HDR-SMood-Challenge-sample.git`

<br>

Clone using the Git Widget:

<img width="566" height="276" alt="Screenshot 2025-12-03 at 8 14 10 AM" src="https://github.com/user-attachments/assets/6cbc9b16-bdd8-4f64-8087-59427c6c2fb5" />

<br>
<br>

### GPU Machine for Beetle Challenge

If you are working on the [Beetle Challenge](https://github.com/jeffgillan/HDR-SMood-Challenge-sample), you can leverage more powerful GPUs from the cloud computer Jetstream2. Go [here](https://github.com/jeffgillan/HDR-SMood-Challenge-sample/tree/main/.github/workflows) to see how. 
