---
title: Predicting NDVI Dynamics
layout: single
author: Rowan Gaffney
author_profile: true
header:
  overlay_color: "444444"
  overlay_image: /assets/images/margaret-weir-GZyjbLNOaFg-unsplash_dark.jpg
---

<!-- Move to Machine Learning section -->

# Distributed Machine Learning: Using Gradient Boosting to Predict NDVI Dynamics

This page was modified from Session 5 of the SCINet Geospatial Workshop 2020. Scientific papers related to NDVI Dynamics listed below:

* [NDVI Dynamics](https://www.ncbi.nlm.nih.gov/pmc/?term=NDVI+dynamics)

**Learning Goals**

- introduction to a preprocessing data pipeline for machine learning
- understand challenges and a set of solutions to distributed computing (via dask distributed) with machine learning
- run a distrubuted machine learning workflow (hyperparameter tuning, training, validation, and model interpretation)

<br><br>

---

## Contents

<!--[Session Rules](#session-rules)-->

[How to Run the Tutorial on Ceres](#how-to-run-the-tutorial-on-ceres)

[View the Tutorial Online](#view-the-tutorial-online)

<br><br>

---

<!--
## Session Rules

**GREEN LIGHT, RED LIGHT** - Use the Zoom participant feedback indicators to show us if you are following along successfully as well as when you need help. To access participant feed back, click on the "Participants" icon to open the participants pane/window. Click the green "yes" to indicate that you are following along successfully, click the red "no" to indicate when you need help. Ideally, you will have either the red or green indicator displayed for yourself throughout the entire tutorial. We will pause every so often to work through solutions for participants displaying a red light.

**CHAT QUESTIONS/COMMENTS TAKE FIRST PRIORITY** - Chat your questions/comments either to everyone (preferred) or to the chat moderator (Rowan Gaffney) privately to have your question/comment read out loud anonamously. We will address chat questions/comments first and call on people who have written in the chat before we take questions from raised hands.

**SHARE YOUR VIDEO WHEN SPEAKING** - If your internet plan/connectivity allows, please share your video when speaking.

**KEEP YOURSELF ON MUTE** - Please mute yourself unless you are called on.
<br><br>

---
-->

## How to Run the Tutorial on Ceres

**Step 1: Login to your SCINet/Ceres account through the JupyterHub web interface**
* Go to [https://jupyterhub.scinet.usda.gov](https://jupyterhub.scinet.usda.gov)
* Login to the system with your SCINet credentials
* Submit the Spawning Page with the following information (if not specified below, leave blank):<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Node Type: ```short```<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Number of Cores: ```4```<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Job Duration: ```02:00:00```<br>

These next two fields are important to enter correctly on the Spawning Page or you will not be able to run the tutorials once you are logged in. Please use copy/paste to avoid mistakes instead of typing these lines:<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Path to the container image: ```/lustre/project/geospatial_tutorials/wg_2020_ws/data_science_im_rs_vSCINetGeoWS_2020.sif```<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Container Exec Args: ```--bind /etc/munge --bind /var/log/munge --bind /var/run/munge --bind /usr/bin/squeue --bind /usr/bin/scancel --bind /usr/bin/sbatch --bind /usr/bin/scontrol --bind /usr/bin/sinfo --bind /system/slurm:/etc/slurm --bind /run/munge --bind /usr/lib64/libslurm.so --bind /usr/lib64/libmunge.so.2 --bind /usr/lib64/slurm --bind  /project --bind /lustre```

After a few minutes, a JupyterLab instance running on the Ceres HPC should open in your browser. After several attempts, if the spawner fails and JupyterLab does not open correctly, please contact the SCINet Virtual Research Support Core (VRSC) for assistance at scinet_vrsc@usda.gov.

**Step 2: Copy the tutorial jupyter notebook file into your home directory**

From inside JupyterLab File > New > Terminal to open a terminal tab.

At the command line

```bash
cp /project/shared_files/GEOSPATIAL_WORKSHOP/session5_machine_learning.ipynb .
```

Note: The original method listed here for accessing our tutorials (from GitHub) was not working for some participants in Session 3. It will be easiest to copy the files from the shared folder on Ceres as above... but an alternate method you can try is to download the tutorial material from the workshop GitHub repo.
* Open a terminal: File-->New-->terminal (alternatively, click the "+" icon (launcher) on the left and then choose the "terminal" icon on the launcher screen)
* Download the tutorials to your home directory
```bash
git clone --single-branch https://github.com/kerriegeil/SCINET-GEOSPATIAL-RESEARCH-WG.git
```

**Step 3: Run a notebook**

* You should now see the file session5_machine_learning.ipynb (in the file system extension on the left hand side of JupyterLab, you may have to click the refresh icon in JupyterLab)
* Double click the session5 file to open it
* Select the py_geo kernel (upper right corner in the notebook)
* Execute blocks of script by clicking the "play" icon in the notebook or typing Shift+Enter

* If you used git clone to get the tutorial Navigate to *~/SCINET-GEOSPATIAL-RESEARCH-WG/tutorials/session5_machine_learning.ipynb*

<br><br>

---

## View the Tutorial Online

If you are not running the tutorial on Ceres during the session you can view a static version of it at [https://kerriegeil.github.io/SCINET-GEOSPATIAL-RESEARCH-WG/html-tutorials/session5_machine_learning.html](https://kerriegeil.github.io/SCINET-GEOSPATIAL-RESEARCH-WG/html-tutorials/session5_machine_learning.html)
