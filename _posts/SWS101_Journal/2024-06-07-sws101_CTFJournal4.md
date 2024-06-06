---
Title: SWS101 CTF Journal 4
categories: [SWS101, CTF_Journal4]
tags: [SWS101]
---

# Try Hack Me Room: Basic Pentesting

![CTF](/pictures/SWS_pictures/basic%20pentesting/basic.png)

## Task1: Web App Testing and Privilege Escalation 

First let’s start the reconnaissance by doing nmap.

![CTF](/pictures/SWS_pictures/basic%20pentesting/nmap.png)

6 ports were open.

Port 80 is open so let’s check the http website

![CTF](/pictures/SWS_pictures/basic%20pentesting/webpage.png)

Oh, it is under maintenance .

### What is the name of the hidden directory on the web server(enter name without /)?
For this we can get the hidden directory with the dirsearch command

![CTF](/pictures/SWS_pictures/basic%20pentesting/diesearch.png)

<b>ANS:</b> development

There is /development directory, let’s check it out

![CTF](/pictures/SWS_pictures/basic%20pentesting/development.png)

There are 2 .txt files. Inside the file, there is a message left by the users.

### dev.txt

![CTF](/pictures/SWS_pictures/basic%20pentesting/dev.png)

### j.txt

![CTF](/pictures/SWS_pictures/basic%20pentesting/j.png)

From these text files I got the following information:
- There are minimum 2 users (J and K, not the real usernames)
- Website is using Apache 2.5.12
- Website is also using SMB (samba)
- User J is having a weak password (most important)

### User brute-forcing to find the username & password
First let’s find out the username, although we know their starting letter, we don't know their full name.

With the smbclient command I found the staff.txt file where their full name was given.

![CTF](/pictures/SWS_pictures/basic%20pentesting/sbm.png)

This is the content of staff.txt.

![CTF](/pictures/SWS_pictures/basic%20pentesting/staff.png)

### What is the username?
<b>ANS:</b> jan

### What is the password?
Since we got the username, now it is easy to brute force the password by using hydra.<br>
The command is : hydra -l jan -P rockyou.txt ssh://10.10.146.4 -I -F -V

![CTF](/pictures/SWS_pictures/basic%20pentesting/password.png)

BOOM! I got the password.

<b>ANS:</b> armando

### What service do you use to access the server(answer in abbreviation in all caps)?
<b>ANS:</b> ssh

### What is the name of the other user you found(all lower case)?
Earlier we found 2 users, Jan and kay.<br>
<b>ANS:</b>kay

### What is the final password you obtain?
When I did ssh login as jan, I got the passphrase and then I used john the ripper to brute force the obtain the final password.<br>
<b>ANS:</b> heresareallystrongpasswordthatfollowsthepasswordpolicy$$

That’s it for this basic pentesting room, see you guys on the next try hack me room walkthrough.
