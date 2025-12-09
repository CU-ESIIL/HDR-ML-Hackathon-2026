# HDR-ML-Hackathon-Boulder-2025
This repo documents resources for the HDR ML Hackathon 2026 event at CU Boulder
<br>
Also see the Indico event page [here](https://indico.cern.ch/event/1615361/)
<br>
<br>
**Learn more about the NSF HDR ML Challenge [here](https://www.nsfhdr.org/mlchallenge-y2) and prize info [here](https://www.codabench.org/competitions/9854/#:~:text=Prize%20Pool%20for%20HDR%20ML%20Challenges%202nd%20year).**
<br>
## Pre-event virtual bootcamp (OPTIONAL)
* Wednesday, December 10, 2025 1:00 PM-3:00 PM
* Zoom link: https://cuboulder.zoom.us/j/95674412181
* Meeting ID: 956 7441 2181

## Event Info
**Where**: [4001 Discovery Dr (SEEC Building)](https://maps.app.goo.gl/G4pHJNsqihCRgLrG8), CU Boulder East Campus

**Zoom info**:  
* [https://cuboulder.zoom.us/j/94963837906](https://cuboulder.zoom.us/j/94963837906) 
* Meeting ID: 949 6383 7906

**Day 1 (main day):**   
* Friday December 12, 2025, 830am - 5pm MST
* Room: VizStudio (SEEC S372)

**Day 2 (office hours, space to work):**  
* Monday December 15, 2025, 830am - 5pm MST
* Room: Sievers Room (SEEC S228)

This event is being organized by:  
* The [National Ecological Observatory Network (NEON), Battelle](https://www.neonscience.org/)
* The [Environmental Data Science Innovation & Impact Lab (ESIIL), CU Boulder](https://esiil.org/)
* The [Imageomics Institute](https://imageomics.org/)
* [CyVerse, University of Arizona](https://cyverse.org/)

## Agenda
### Day 1 (Friday, December 12):  
* 0830-0900 - Arrive and get set up. Coffee will be provided!
* 0900-0920 - Welcome from [NEON](https://neonscience.org) and [ESIIL](https://esiil.org/)
* 0920-1000 - Introductions and Ice breaker
* 1000-1030 - Overview of [challenge themes](https://hdr-ecosystem.github.io/y2-challenge-webpage/index.html)
    * Imageomics - Beetles as sentinel taxa
    * A3D3 - Neurobiology
    * iHarp - Predicting coastal flooding
* 1030-1040 - Break
* 1040-1100 - Getting started with compute resources
    * [CyVerse DE](https://de.cyverse.org) overview
* 1100-1200 - How to create a submission
    * Overview of Codabench pages
        * Beetles as Sentinel Taxa (Imageomics): https://www.codabench.org/competitions/9854/
        * Predicting Coastal Flooding (iHARP): https://www.codabench.org/competitions/10801/
        * Neural Forecasting (A3D3): https://www.codabench.org/competitions/9806/
    * Overview of baseline models/submissions
    * How to submit - Imageomics submission example
* 1200-1300 - Lunch break! Lunch will be provided!
* 1300-1400 - Recap, continue with baseline submission exercise
* 1400-1600 - Breakouts to form teams, work on challenge
* 1600-1630 - Report outs and wrap up. 

### Day 2 (Monday, December 15):  
* 0830-0900 - Coffee, get settled
* 0900-0930 - Brief check-in, do groups need help with anything?
    * Organize breakouts if needed. 
    * Match CyVerse and/or theme leads with groups that may need help
* 0930-1130 - Free time to work
* 1130-1200 - Check in with groups. Report out and Wrap up.
* 1200-1300 - Lunch break
* 1300-1600 - NEON Tour ([walk to NEON HQ](https://maps.app.goo.gl/2Bh1vjLpaYdrZnVUA))

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

#### Sharing Folders
<img width="464" height="405" alt="Screenshot 2025-12-03 at 8 26 32 AM" src="https://github.com/user-attachments/assets/a241c32d-4104-4907-a3c2-77a5679a4c5c" />

<img width="405" height="167" alt="Screenshot 2025-12-03 at 8 28 44 AM" src="https://github.com/user-attachments/assets/58b542bd-65b3-4aad-a8c6-d47f37ba0938" />

<br>
<br>

### Apps

Launching [ESIIL ML Challenge 2025](https://de.cyverse.org/apps/de/165baf1e-be83-11f0-bf87-008cfa5ae621)

Command line navigation


<img width="385" height="211" alt="Screenshot 2025-12-09 at 1 58 09 PM" src="https://github.com/user-attachments/assets/06672706-4fd9-47e3-9be5-4344ec8fbd40" />

<br>
<br>

#### Authenticate with Github
Authenticating with Github allows you to push changes back up to a repository. 

In the terminal of jupyterlab, authenticate to github by typing:

`gh auth login` 

Follow the prompts to connect the DE app with your Github account

<br>
<br>

#### Clone repository to App

Best practices would be to clone git repositories to the directory `~/data-store` within the Cyverse App.

Clone using the Terminal:

`git clone --branch <branch-name> https://github.com/jeffgillan/HDR-SMood-Challenge-sample.git`

<br>

Clone using the Git Widget:

<img width="566" height="276" alt="Screenshot 2025-12-03 at 8 14 10 AM" src="https://github.com/user-attachments/assets/6cbc9b16-bdd8-4f64-8087-59427c6c2fb5" />

