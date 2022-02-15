---
layout: default
---

# Lab Report 3 – Week 6
## Copy whole Directories with `scp -r` and streamlining multiple commands

> **Lab overview and tasks:**
>>In this quick blog post, we will cover copying our an entire directory from a previous project into our ***ieng6*** account. To check for a successful transfer, we will compile and run the tests for our copied repository in our `ieng6` account. Lastly, we will demonstrate how to streamline this proccess further and combine the `ieng6` and `ssh` commands to copy whole directories and run the tests - all in one line and remotely -> from our local workstation.

# ┬┴┬┴┤ᵒᵏ (･_├┬┴┬┴
***

### Moving Whole Directories over SSH with `scp -r`
One key step in working remotely is being able to copy files back and forth between computers. However, in order to remote copy entire directories - we must include the **-r** flag. 
> As a refresher to week 1's lab in blog report 1, we will include the scp -r command structure below:
>> `scp [path to be copied] [remote path to paste the copy] `


In this example, we will show how to copy our local mardown-parse directory and all its contents into our ieng6 account - using the following line of code:
> `$ scp -r . cs15lwi22@ieng6.ucsd.edu:~/markdown-parse`

The -r option tells scp to work recursively. The . is the current directory we are in, and is the directory that will be copied. The ~/markdown-parse tells scp to create the markdown-parse directory on the remote server (if it doesn’t exist), and then copy the contents of this directory recursively into that new directory.
Let's see this in action:
<video src="assets\images\week6-report3-vid_A.mp4" controls="controls" style="max-width: 1000px;"></video>

## Making Remote Running Even More Pleasant
>#### From Lab 1, we learned that:
>* we can use semicolons to run multiple commands on the same line in most terminals. For example: <br>`⤇ cp WhereAmI.java Copies/WhereaAmI.java; javac SomeOtherMain.java; java SomeOtherMain`
>* and we can write a command in quotes at the end of an ssh command to directly run it on the remote server, then exit. For example, this command will log in and list the home directory on the remote server: <br>`⤇ ssh cs15lwi22@ieng6.ucsd.edu "ls"`<br>
In that case, let's try using this command to copy the whole directory and run the tests in one line. <br>
<pre>⤇ scp -r . cs15lwi22zzz@ieng6.ucsd.edu:~/markdown-parse ; ssh -t cs15lwi22aog@ieng6.ucsd.edu "cd markdown-parse-linux/ ; make test"</pre>

### *was there an error? Why?*

After some research I learned the difference between ***Login Shells vs Interactive ...***
>* [Bash Startup Explained](https://zwischenzugs.com/2019/02/27/bash-startup-explained/) ***-AND-***

>* From [ssh(1) manual page](https://linux.die.net/man/1/ssh): "If command is specified, it is executed on the remote host instead of a login shell."

>>* *So in short, when you only login to the machine `[ssh]` -> bash is started as a login shell and loads the apropriate `~/.bash_profile` **enviroment paths**.*

>>* *However, when you connect remotely and issue a command enclosed as a "string" -> you’re in an **interactive non-login shell*** 

>>>* *As a result, this will only load **~/.bashrc script**, since it assumes that the enviroment is already set up. Actually, it's not set-up this way in our case. This means our enviroment paths are inherited from local machine or not found at all!*

### To force a login to simulate a login shell after passing commands and run the commands w/ the appropriate path variables ⤇ we will run **ssh** and pass the `"bash --login"` string command ⤇ then within the simulated login shell we will pass in `-c 'env commands'` as a string within the first string... More importantly, to simulate the login shell remotely ⤇ we must include th `-t` flag after **ssh** to force pseudo-tty allocation, otherwise all else will not work!

In our case, we will demonstrate this trick using the following command <br>
<pre>⤇ scp -r . cs15lwi22zzz@ieng6.ucsd.edu:~/markdown-parse ; ssh -t cs15lwi22zzz@ieng6.ucsd.edu "bash --login -c 'cd markdown-parse/;make test'"</pre><br>in the vid below:

<video src="assets\images\week6-report3-vid_B.mp4" controls="controls" style="max-width: 1000px;"></video>

### [Check this page out for more ssh explanations](https://explainshell.com/explain?cmd=ssh+-t+my_host+my_command)



***
<audio preload="metadata" controls loop autoplay>
  <source src="assets\images\Tower of Lahja - Ninja Gaiden II_ The Dark Sword of Chaos (128 kbps).mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>