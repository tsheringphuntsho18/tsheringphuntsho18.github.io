---
Title: Seasonal CTF Joutnal 1
categories: [CTF, CTF_walkthrough]
tags: [SWS202]
---
"<span style="color:yellow">*Be black or white, don’t try to be grey.*</span>"

![cover](/pictures/SWS_pictures/darkcorp/cover.png)


### Room Information
- Room Name: Darkcorp
- Difficulty Level: Insane
- Room type: Seasonal machine(CTF)
- Platform: Hack the box

### Reconnaissance

Let’s run nmap and check what ports are open.

![cover](/pictures/SWS_pictures/darkcorp/nmap.png)

We have discovered 2 open ports: 22(ssh) and 80(http). Since port 80 is open let’s check the website.

![cover](/pictures/SWS_pictures/darkcorp/404.png)

We can see that the website redirects us to “drip.htb”, so let’s add that to our hosts file.

![cover](/pictures/SWS_pictures/darkcorp/nano.png)

Let’s refresh the website.

![cover](/pictures/SWS_pictures/darkcorp/website.png)

I found that it is a mailing website. Next I try that functionality of that dripmail.

![cover](/pictures/SWS_pictures/darkcorp/contactus.png)

the contact us is working fine and my message is sent successfully. I have also sign up to that dripmail site.

![cover](/pictures/SWS_pictures/darkcorp/signup.png)

![cover](/pictures/SWS_pictures/darkcorp/signup2.png)

But the sign in is blocking by firewall.

![cover](/pictures/SWS_pictures/darkcorp/signin.png)

I notice that it is re-directed to “mail.drip.htb”. 

Let’s add that to our host file.( sudo nano /etc/hosts)

![cover](/pictures/SWS_pictures/darkcorp/mailnano.png)

When refreshed, I got the login form. 

![cover](/pictures/SWS_pictures/darkcorp/mail.png)

So I used my credential that i signup.

![cover](/pictures/SWS_pictures/darkcorp/htbmail.png)

I was welcome by gmail like page. 

Next i also try to search for subdirectory.

![cover](/pictures/SWS_pictures/darkcorp/dirsearch.png)

I found dashboard sudirectory, let'c check that.

![cover](/pictures/SWS_pictures/darkcorp/dashboard.png)

ohh, that page is not found. Now i am struck.


