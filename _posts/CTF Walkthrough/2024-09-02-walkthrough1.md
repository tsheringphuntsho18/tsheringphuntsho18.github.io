---
Title: CTF Walkthrough 1
categories: [CTF, CTF_walkthrough]
tags: [CTF]
---

"<span style="color:yellow">*Remember, hacking is more than just a crime. It's a survival trait.*</span>"

![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/cover.png)

### Room Information
 - Room Name: U.A. High School
 - Difficulty Level: Easy
 - Room type: Challenges(CTF)

![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/machine.png)

### Reconnaissance
let’s run nmap and check what ports are open
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/nmap.png)
I discovered 2 open ports: 22 and 80,. Since port 80 is open, let’s check the website.

![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/website.png)
It is just a normal high school website. 

So let’s check for any other hidden directories using dirsearch.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/dirsearch.png)
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/hiddendir.png)
I found that there is a hidden directory (/assets). Let’s check /assets.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/blank.png)

The directory is simply a blank page. Let’s proceed further by finding the subdirectory.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/subdir.png)
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/hiddensubdir.png)
I found the index.php subdirectory. So there is the possibility of command injection.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/cmd.png)
Let’s begin the command injection
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/ls.png)
Oh, I got the base64. Let's crack it using cyberchef.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/base64.png)
I already knew there were subdirectories like images, index.php, or styles.css. So this confirms that we can perform command injection. 
Let’s Try with the cat passwd
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/catpasswd.png)

Again base64, let’s crack it using cyberchef.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/user.png)
deku:x:1000:1000:deku:/home/deku:/bin/bash
From the last line, I got the user(deku). 


### Now Let’s get to the User.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/hydra.png)

To log in using ssh, I try to brute force Deku’s password using the hydra command and I try to file that contains passwords. I could not found in the first file and rockyou.txt took lots of time to complete. So let’s do using the reverse shell.

Let's get a reverse connection using Netcat
Start netcat listener 
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/nc.png)

Go to https://www.revshells.com/ and generate the reverse shell as below.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/reverseshell.png)

Click on copy and then paste it into the URL after cmd= 
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/paste.png)
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/connection.png)

Wow, I received the connection.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/image.png)
Run command: python3 -c 'import pty;pty.spawn("/bin/bash")' to use /bin/bash

Inside the images directory, there are 2 images.

Let’s Transfer these files from the Victim’s machine to the attacker’s system using Netcat.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/sender.png)
We send files like this. And in another terminal, we receive like this;
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/receiver.png)

Let’s check if I received it or not
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/isthere.png)

upon further inspection found that the file uses the extension .jpg but is in data format. So we are going to Change the incorrect jpg file headers. 

Opening the file using Hexedit.
Command: hexedit oneforall.jpg
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/header.png)
Change the initial header to FF D8 FF E0  00 10 4A 46  49 46 00 01  01 00 00 01. This is the correct signature for the jpeg file. Save the file.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/show.png)
Now it is showing the correct extension for the image and I can also view the image.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/pic.png)


Now using this file we can use stegnography to check file contents
Using steghide to extract the files inside the file
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/steghide.png)

Oh, we need to enter the passphrase, earlier I found the hidden file and it contains the base64 code.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/hiddencontent.png)
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/pass.png)
So the passphrase is AllmightForEver!!!
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/password.png)
wow, finally I got the password for Deku.

Using the password that I got, I can easily log in to Duke using ssh. 
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/ssh.png)

There is a user.txt file. I got the user flag. 

### Privilege Escalation
The next task is to get the root.txt flag. It isn’t as easy as I thought. I can’t get into root just with the command sudo su.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/su.png)

I need to check for sudo privileges.
Command: sudo -l
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/-l.png)

User deku can run (ALL) /opt/NewComponent/feedback.sh. Let’s do what user deku is allowed to do. 
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/feedback.png)
Deku can give feedback. Let’s try to give malicious feedback.
The malicious feedback is ‘Deku ALL=NOPASSWD: ALL >> /etc/sudoers’
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/root.png)
It works and now I got the root access.
![cover](/pictures/SWS_pictures/write_up/U.AhighSchool/rootflag.png)
Finally, I also got the root.txt

### Flag Captured
- user.txt flag: THM{W3lC0m3_D3kU_1A_0n3f0rAll??}

- root.txt flag:  THM{Y0U_4r3_7h3_NUm83r_1_H3r0}
