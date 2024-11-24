---
Title: CTF Walkthrough 5
categories: [CTF, CTF_walkthrough]
tags: [CTF]
---
"<span style="color:yellow">*There is no right and wrong. There's only fun and boring.*</span>"

![cover](/pictures/SWS_pictures/write_up/lookup/cover.png)

### Room Information
- Room Name: Lookup
- Difficulty Level: Easy
- Room type: Challenges(CTF)

![cover](/pictures/SWS_pictures/write_up/lookup/machine.png)

### Reconnaissance
![cover](/pictures/SWS_pictures/write_up/lookup/info.png)

Let’s run nmap and check what ports are open.

![cover](/pictures/SWS_pictures/write_up/lookup/nmap.png)

We have discovered 2 open ports: 22(ssh) and 80(http). Since port 80 is open let’s check the website.

![cover](/pictures/SWS_pictures/write_up/lookup/lookup.png)

We can see that the website redirects us to “lookup.thm”, so let’s add that to our hosts file.

![cover](/pictures/SWS_pictures/write_up/lookup/nano.png)

Let’s refresh the website.

![cover](/pictures/SWS_pictures/write_up/lookup/website.png)

It shows the login form. 

![cover](/pictures/SWS_pictures/write_up/lookup/wrong.png)

We don’t have user credentials so we can write a small python script that would help us enumerate valid usernames:

![cover](/pictures/SWS_pictures/write_up/lookup/script.png)

![cover](/pictures/SWS_pictures/write_up/lookup/user.png)

When I ran that python script I got two usernames;
- admin
- jose

Now let’s brute force the password using hydra.<br>
Command: hydra -l jose -P /path/to/rockyou.txt lookup.thm http-post-form "/login.php:username=^USER^&password=^PASS^:Wrong" -V

![cover](/pictures/SWS_pictures/write_up/lookup/password.png)

When we login we have been re-directed to “files.lookup.thm”. 

![cover](/pictures/SWS_pictures/write_up/lookup/file.png)

Let’s add that to our host file.( sudo nano /etc/hosts)

![cover](/pictures/SWS_pictures/write_up/lookup/add.png)

When refreshed, We landed in something called “elFinder”. This looks like a file manager.

![cover](/pictures/SWS_pictures/write_up/lookup/filesite.png)

Start metaexploit and search for elfinder. 

![cover](/pictures/SWS_pictures/write_up/lookup/elfinder.png)

Use exploit/unix/webapp/elfinder_php_connector_exiftran_cmd_injection

![cover](/pictures/SWS_pictures/write_up/lookup/run.png)

Drop shell and use netcat.

![cover](/pictures/SWS_pictures/write_up/lookup/shell.png)

![cover](/pictures/SWS_pictures/write_up/lookup/netcat.png)

Once we receive the connection.<br>
Run this command: python3 -c 'import pty;pty.spawn("/bin/bash")'

### Now Let’s get to the User. 

We do have user think. 

![cover](/pictures/SWS_pictures/write_up/lookup/think.png)

![cover](/pictures/SWS_pictures/write_up/lookup/perme.png)

We need to login as a user think to get user.txt flag.

Let’s search for SUID binaries:
Command: find / -perm /4000 2>/dev/null

![cover](/pictures/SWS_pictures/write_up/lookup/suid.png)

The /usr/sbin/pwm binary draws my attention because it's not there by default on Linux hosts.

Let’s try to trick the program into executing a different “ID” command, one that would result in the “think” username being extracted from the output.<br>
We can add /tmp to our path:

![cover](/pictures/SWS_pictures/write_up/lookup/way.png)

And now create /tmp/id. When we try running pwm we get the password list for user think. 

![cover](/pictures/SWS_pictures/write_up/lookup/list.png)

Now let’s save those lists and brute force the password using hydra.

Command: hydra -l think -P /home/tshering/THM/password.txt 10.10.211.78 ssh

![cover](/pictures/SWS_pictures/write_up/lookup/brute.png)

Username: think 
Password: josemario.AKA(think)

With those credentials let’s login to ssh.

![cover](/pictures/SWS_pictures/write_up/lookup/ssh.png)

Finally, boom…..we got the user flag. 

### Privilege Escalation
Now let’s try to get into a root.

![cover](/pictures/SWS_pictures/write_up/lookup/-l.png)

think can run /usr/bin/look. Let’s search in gtfobin 

![cover](/pictures/SWS_pictures/write_up/lookup/gtfo.png)

Let’s run it.

![cover](/pictures/SWS_pictures/write_up/lookup/id_rsa.png)

We got the id_rsa for the root, now save it, and let’s use it to login to root.

![cover](/pictures/SWS_pictures/write_up/lookup/root.png)

Now I have root access. 

![cover](/pictures/SWS_pictures/write_up/lookup/rootflag.png)

Finally, I got the root.txt


### Flag Captured
user.txt flag: 38375fb4dd8baa2b2039ac03d92b820e<br>
root.txt flag:  5a285a9f257e45c68bb6c9f9f57d18e8

