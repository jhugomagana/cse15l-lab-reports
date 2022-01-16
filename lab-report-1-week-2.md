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

### Remotely Connecting
> ***Before you connect***
>> if we’re on a Windows machine: install this program first - <a href="hhttps://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse">OpenSSH</a>
>> Then, jot down your course-specific account for CSE15L using the <a href="https://sdacs.ucsd.edu/~icc/index.php">Account Lookup tool</a> and it should look familiar to this:
```bash
cs15lwi22zz
```

Moving on to VSCode press **Ctrl** or **Command + `**, or use the Terminal → New Terminal menu option to open up a ***terminal***.
>> *from here on out, our command will look like the one below, but with the **zz** replaced to reflect our individual and unique course-specific account sequence (note also that term/year will change).*

```bash
$ ssh cs15lwi22zz@ieng6.ucsd.edu
```
<video src="assets\images\ssh_ieng6_VScode.mp4" controls="controls" style="max-width: 1000px;">
</video>

### Trying Some Commands

### Moving Files with **`scp`**

### Setting an SSH Key

### Optimizing Remote Running