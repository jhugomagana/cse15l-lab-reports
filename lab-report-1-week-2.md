---
layout: default
---

# Lab Report 1 – Week 2
## Remote Access into the `ieng6` Server
> **Lab overview and tasks:**
>> In this blog, we will cover how to set our computer up for remote access into the **CSE Dungeon** computers. If you're in this *class*, or likey any other ***CSE course***, we will need to find your *<mark>CSE course-specific account</mark>* in order to **`ssh`** from your local computer into the **`ieng6`** server holding the account. There are many ways to accomplish this connection, but for now we will use **Visual Studio Code's** remote option, via the IDE's integrated terminal. Following a successful connection, we will test out a few **Unix-like commands** and familiarize with the ***Linux Filesystem***. One command in particular, **`scp`**, will come in handy to transfer files over <mark>SSH</mark>. Lastly, we will generate our own unique *<mark>SSH Keys</mark>* and further ***optimize remote running*** over the command line :)  

# ┬┴┬┴┤ᵒᵏ (･_├┬┴┬┴
***

### Installing VScode
First, we need to head over to the <a href="https://code.visualstudio.com/">Visual Studio Code website</a>, and follow the instructions there to download the appropriate version for our OS and install it onto our computer. Once installed, we should be able to open a window that looks like this (note that depending on our system/settings, it may reflect different colors or menu bar):

<img src="assets\images\000.JPG" alt="VScode" width="1000"/>

<!-- ![fun jelly placeholder](https://cdn.vox-cdn.com/thumbor/itq6pDCz1YU_jpjTVLhVwxnqBjU=/46x0:552x337/1400x1400/filters:focal(46x0:552x337):format(gif)/cdn.vox-cdn.com/uploads/chorus_image/image/49497833/jelly.0.0.gif) -->
### Remotely Connecting
> ***Before you connect***
>> if we’re on a Windows machine: install this program first - <a href="hhttps://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse">OpenSSH</a>
>> Then, jot down your course-specific account for CSE15L using the <a href="https://sdacs.ucsd.edu/~icc/index.php">Account Lookup tool</a> and it should look familiar to this:
```cs15lwi22zz```

Moving on to VSCode press **Ctrl** or **Command + `**, or use the Terminal → New Terminal menu option to open up a ***terminal***.
>> *from here on out, our command will look like the one below, but with the **zz** replaced to reflect our individual and unique course-specific account sequence (note also that term/year will change).*

```bash
$ ssh cs15lwi22zz@ieng6.ucsd.edu
```
below is also a quick demo for reference:

<video src="assets\images\ssh_ieng6_VScode.mp4" controls="controls" style="max-width: 1000px;">
</video>
In case it is your first time logging into your account over ssh, you might come across this message below before entering your password. If this is true, enter {yes} and proceed to entering your password - see below for reference:
```bash
ssh cs15lwi22zz@ieng6.ucsd.edu # press enter
The authenticity of host 'ieng6-202.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? # type - yes
Password:
Last login: Sun Jan  2 14:03:05 2022 from 107-217-10-235.lightspeed.sndgca.sbcglobal.net
quota: No filesystem specified.
Hello cs15lwi22zz, you are currently logged into ieng6-203.ucsd.edu

You are using 0% CPU on this system

Cluster Status
Hostname     Time    #Users  Load  Averages  
ieng6-201   23:25:01   0  0.08,  0.17,  0.11
ieng6-202   23:25:01   1  0.09,  0.15,  0.11
ieng6-203   23:25:01   1  0.08,  0.15,  0.11

Sun Jan 02, 2022 11:28pm - Prepping cs15lwi22
[cs15lwi22zz@ieng6-203]:~:31$
```

### Trying Some Commands
Try running the commands `cd`, `ls`, `pwd`, `mkdir`, and `cp` a few times on both your computer and on the remote computer - note that some of these commands are not recognized on **Windows cmd** until you you ssh into the remote computer's **bash shell**

### Moving Files with **`scp`**

### Setting an SSH Key

### Optimizing Remote Running