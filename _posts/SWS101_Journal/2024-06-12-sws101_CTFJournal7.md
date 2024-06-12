---
Title: SWS101 CTF Journal 7
categories: [SWS101, CTF_Journal7]
tags: [SWS101]
---

# Try Hack Me Room: Wgel CTF
![CTF](/pictures/SWS_pictures/wgel/wgel.png)

Let’s run nmap and check what ports are open

![CTF](/pictures/SWS_pictures/wgel/nmap.png)

We discovered 2 open ports 22 and 80 

Since port 80 is up, let’s check the website.

![CTF](/pictures/SWS_pictures/wgel/website.png)

It’s just a normal Apache2 page.

## Task1: Wgel CTF
With the ffuf, let’s check for the directories.

![CTF](/pictures/SWS_pictures/wgel/sitemap.png)

There are only sitemap directories.

![CTF](/pictures/SWS_pictures/wgel/only.png)

When i check it’s only a website. Let's find further directories. There is .ssh, when I access the site, I can see an ssh key available. Let’s grab it and try to get an ssh session.

![CTF](/pictures/SWS_pictures/wgel/ssh.png)

Inside the the is_rsa file there is a private key

![CTF](/pictures/SWS_pictures/wgel/rsa.png)

![CTF](/pictures/SWS_pictures/wgel/id_rsa.png)

Got id_rsa file. Let's try to crack it. Lets try to login with ssh. To get the SSH session we need a username to connect with this key. Remember there was a name commented there (Jessie). I am going to use it.

![CTF](/pictures/SWS_pictures/wgel/jessie.png)

### User flag

![CTF](/pictures/SWS_pictures/wgel/user_flag.png)

<b>ANS:</b> 057c67131c3d5e42dd5cd3075b198ff6

### Root flag
Now it’s time to get root access. The procedure will be walkthrough in part.<br>
<b>ANS:</b>  b1b968b37519ad1daa6408188649263d
