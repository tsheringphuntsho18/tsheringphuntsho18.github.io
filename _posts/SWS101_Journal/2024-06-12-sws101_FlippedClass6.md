---
Title: SWS101 CTF Journal 6
categories: [SWS101, CTF_Journal6]
tags: [SWS101]
---

# Try Hack Me Room: Anthem
![CTF](/pictures/SWS_pictures/Anthem/anthem.png)

## Task1: Website Analysis
Let's run nmap and check what ports are open.

![CTF](/pictures/SWS_pictures/Anthem/anthemnmap.png)

We discovered 2 open ports 80 and 3389.

### What port is for the web server?
<b>ANS:</b> 80

### What port is for remote desktop service?
<b>ANS:</b> 3389

Since port 80 is open, let’s check what is there on the website.

![CTF](/pictures/SWS_pictures/Anthem/website.png)

### What is a possible password in one of the pages web crawlers check for?
Checking /robots.txt directories.

![CTF](/pictures/SWS_pictures/Anthem/robot.png)

<b>ANS:</b> UmbracoIsTheBest!

### What CMS is the website using?
The server is running Umbraco CMS.<br>
<b>ANS:</b> Umbraco

### What is the domain of the website?
In the website itself, it was mentioned that anthem.com<br>
<b>ANS:</b> anthem.com

### What's the name of the Administrator
![CTF](/pictures/SWS_pictures/Anthem/admin.png)

In this page, there is a poem written for the administrator and i copy pasted that poem in google and got the admin name.

![CTF](/pictures/SWS_pictures/Anthem/poem.png)

<b>ANS:</b> Solomon Grundy

### Can we find the email address of the administrator?
![CTF](/pictures/SWS_pictures/Anthem/jd.png)

The email for Jane Doe is JD@anthem.com and for admin Solomon Grundy
It will obviously SG@anthem.com<br>
<b>ANS:</b> SG@anthem.com

## Task2: Spot the flags
Our beloved admin left some flags behind that we require to gather before we proceed to the next task…

<span style="color:red">Answer the questions below</span>.

Let’s answer this question by reading the hint.

### What is flag 1?
Hint{Have we inspected the pages yet?}<br>
Oh let’s inspect the pages. After brute forcing each page I got the flag on the hiring page. 

![CTF](/pictures/SWS_pictures/Anthem/flag1.png)

<b>ANS:</b> THM{L0L_WH0_US3S_M3T4}

### What is flag 2?
Another flag is on the hiring page.

![CTF](/pictures/SWS_pictures/Anthem/flag2.png)

<b>ANS:</b> THM{G!T_G00D}

### What is flag 3?
Hint{Profile}
Let’s check profile

![CTF](/pictures/SWS_pictures/Anthem/flag3.png)

<b>ANS:</b> THM{L0L_WH0_D15}

### What is flag 4?

![CTF](/pictures/SWS_pictures/Anthem/flag4.png)

<b>ANS:</b> THM{AN0TH3R_M3TA}

## Task3: Final stage
Let's get into the box using the intel we gathered.

<span style="color:red">Answer the questions below</span>.<br>
Let's figure out the username and password to log in to the box.(The box is not on a domain)

### Gain initial access to the machine, what is the contents of user.txt?
As we already know that we have a remote desktop port 3389 open, we use the already found credentials to log in.<br>
Username — SG<br>
Password — UmbracoIsTheBest!<br>

Command is rdesktop -u SG -p UmbracoIsTheBest! 10.10.206.13

![CTF](/pictures/SWS_pictures/Anthem/window.png)

Wow window desktop gets open and there is also a user file.

![CTF](/pictures/SWS_pictures/Anthem/user.png)

<b>ANS:</b> THM{N00T_NO0T}

### Can we spot the admin password?
Hint{It is hidden.}<br>
There is a backup folder that has the password required to access the Administrator folder. 

![CTF](/pictures/SWS_pictures/Anthem/afolder.png)

<b>ANS:</b> ChangeMeBaby1MoreTime

### Escalate your privileges to root, what is the contents of root.txt?
<b>ANS:</b>THM{Y0U_4R3_1337}

That’s it for this anthem room, see you guys on the next try hack me room walkthrough.
