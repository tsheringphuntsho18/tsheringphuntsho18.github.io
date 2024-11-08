---
Title: CTF Walkthrough 3
categories: [CTF, CTF_walkthrough]
tags: [CTF]
---
"<span style="color:yellow">*The superior man, when resting in safety, does not forget that danger may come*</span>"


![cover](/pictures/SWS_pictures/write_up/NinjaSkill/cover.png)

### Room Information

- Room Name: Ninja Skills
- Difficulty Level: Easy
- Room type: Challenges(CTF)

![cover](/pictures/SWS_pictures/write_up/NinjaSkill/machine.png)

### Reconnaissance

The Ninja Skills room is a beginner-level room that focuses on basic Linux commands, more specifically the “find” command.

![cover](/pictures/SWS_pictures/write_up/NinjaSkill/info.png)

They have given us the user credentials
- Username: new-user
- Password: new-user

First, ssh into the machine.

![cover](/pictures/SWS_pictures/write_up/NinjaSkill/ssh.png)

### Now let’s answer the questions.

<b> Which of the above files are owned by the best-group group(enter the answer separated by spaces in alphabetical order) </b>

Command: find / -type f -group best-group 2>>/dev/null

![cover](/pictures/SWS_pictures/write_up/NinjaSkill/find1.png)

ANS: D8B3 v2Vb


<b> Which of these files contain an IP address? </b>

Command: find / -type f \( -name 8V2L -o -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -name X1Uy \) -exec grep -E -o "([0-9]{1,3}[\.]){3}[0-9]{1,3}" * {} \; 2>>/dev/null

I told the command to search all the files. In those files, the -exec tells the find command to “execute” a command on each file that it finds, the command is to validate IPv4 addresses in a file, using regex.

![cover](/pictures/SWS_pictures/write_up/NinjaSkill/find2.png)

ANS: oiMO

<b> Which file has the SHA1 hash of 9d54da7584015647ba052173b84d45e8007eba94 </b>

Command: find / -type f \( -name 8V2L -o -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -name X1Uy \) -exec sha1sum {} \; 2>>/dev/null

To find the files with SHA1 we have to use sha1sum.

![cover](/pictures/SWS_pictures/write_up/NinjaSkill/find3.png)

ANS: c4ZX

<b> Which file contains 230 lines?</b>

Command: find / -type f \( -name 8V2L -o -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -name X1Uy \) -exec wc -l {} \; 2>>/dev/null

![cover](/pictures/SWS_pictures/write_up/NinjaSkill/find4.png)

The only file that’s NOT listed with this command is the flag.

ANS: bny0

<b> Which file's owner has an ID of 502? </b>

Command:  find / -type f \( -name 8V2L -o -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -name X1Uy \) -exec ls -ln {} \; 2>>/dev/null

![cover](/pictures/SWS_pictures/write_up/NinjaSkill/find5.png)

ANS: X1Uy

<b> Which file is executable by everyone?</b>

The file with the “x” indicates that everyone is able to execute on this file.

![cover](/pictures/SWS_pictures/write_up/NinjaSkill/find5.png)

ANS: 8V2L


### Conclusion
In this room, we only need to enter the correct command to be able to answer those questions. Unlike other CTF rooms, we don’t need to get the user and root flags. If you are stuck with how to give the correct command, then google it.
