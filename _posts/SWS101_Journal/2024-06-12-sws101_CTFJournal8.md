---
Title: SWS101 CTF Journal 8
categories: [SWS101, CTF_Journal8]
tags: [SWS101]
---

# Try Hack Me Room: Corridor
Can you escape the Corridor?

![CTF](/pictures/SWS_pictures/corridor/corridor.png)

Let’s run nmap and check what ports are open.

![CTF](/pictures/SWS_pictures/corridor/nmap.png)

we discovered only 1 open port 80. Let’s check the website.

![CTF](/pictures/SWS_pictures/corridor/website.png)

Task1: Escape the Corridor
Let’s get into the first room.

![CTF](/pictures/SWS_pictures/corridor/room1.png)

Each door has a door number and when clicked gets directed to a webpage with a URL — http://IP/<md5-value-of-the-door-number>

### What is the flag?
When we inspect, these are md5 hash values of numbers.

![CTF](/pictures/SWS_pictures/corridor/inspect.png)

When we crack that hash it is showing numbers 1 to 13 and the hidden door is number 0.<br>
Let’s generate md5 hash for 0 

![CTF](/pictures/SWS_pictures/corridor/md5.png)

Now paste that hash in url like this machine_ip/hash

![CTF](/pictures/SWS_pictures/corridor/flag.png)

Boom! We got the flag.<br>
<b>ANS:</b> flag{2477ef02448ad9156661ac40a6b8862e}

That’s it for this corridor room, see you guys on the next try hack me room walkthrough.
