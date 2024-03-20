---
Title: SWS101 Flipped Class 2
categories: [SWS101, Flipped_class2]
tags: [SWS101]
---

## Topic: Hack The Box : Starting Point

### Introduction
Hack The Box is the hacking playground and cybersecurity community in the world founded by Haris Pylarinos. Its Starting Point machines serve as an excellent entry point for beginners which makes us understand the basics of penetration testing. I am a beginner to cyber security and chose to start from the starting point machine. Starting points consist of 3 tier(tier0, tier1 and tier 2),  in this journal i will be going  through tier0 and tier1. Note that to answer the challenges under each tier, we need to connect to the hack the box VPN.

### TIER 0 (The key is a strong foundation)
From tier 0, I have gained essential skills in pen-testing. I learned how to connect to various services, such as ftp, smb and telnet  anonymously. I also learned how to use nmap to identify open ports. In this tier there are many virtual machines but some are locked and can only be answered by purchasing premium. So the virtual machines that I will be going through in this tier are Meow, Fawn, Dancing and Redeemer.

#### 1. Meow
Task 1 

![htb](pictures/htb1.png)

Task 2

![htb](pictures/htb2.png)

Task 3

![htb](pictures/htb3.png)

As mentioned above, we need to form a VPN connection into HTB labs. To do so we need to use the openvpn service followed by /path/to VPN that we downloaded from hack the box.

Command :
 sudo openvpn /home/tshering/Downloads/starting_point_emptyboxInside.ovpn

Task 4: What tool do we use to test our connection to the target with an ICMP echo request?

Ans: ping

![htb](pictures/htb4.png)

Task 5

![htb](pictures/htb5.png)

Task 6: What service do we identify on port 23/tcp during our scans?

Ans: telnet

![htb](pictures/htb6.png)

After scanning, on port 23/tcp I identify a telnet service . TELNET (TErminaL NETwork) is a type of protocol that enables one computer to connect to a local computer.

Task 7

![htb](pictures/htb7.png)

Task 8: Summit root flag

To CTF(capture the flag), I need to connect with the target machine IP address.

![htb](pictures/htb8.png)

Root is the username that I can login with password.
With the “ls” command, all the files and folders inside that directory will be displayed.

![htb](pictures/htb8a.png)

There is a flag.txt file, so to display the content inside that file the command is “cat”

![htb](pictures/htb8c.png)

Flag is b40abdfe23665f766f9c61ecba8a4c19


#### 2. Fawn
Task 1

![htb](pictures/htbf1.png)

Task 2: Which port does the FTP service listen on usually?

![htb](pictures/htbf2n5.png)

Ans: 21

Task 3

![htb](pictures/htb3.png)

Task 4

![htb](pictures/htbf4.png)

Task 5: From your scans, what version is FTP running on the target?

![htb](pictures/htbf2n5.png)

Ans: vsftpd 3.0.3

Task 6: From your scans, what OS type is running on the target?

![htb](pictures/htbf6.png)

Ans: Unix

Task 7

![htb](pictures/htbf8.png)

Task 8

![htb](pictures/htbf8.png)

Task 9: What is the response code we get for the FTP message 'Login successful'?

![htb](pictures/htbf9.png)

We have to login using the ftp command. As we covered in task 8, the username to log into ftp is anonymous and password is the default one i.e ‘password’.

Ans: 230

Task 10

![htb](pictures/htbf10.png)

Task 11

![htb](pictures/htbf11.png)

Task 12 : Submit root flag

![htb](pictures/htbfflag.png)

I listed the files and folders inside ftp and found that there is a flag.txt file but I can't display that file with the ‘cat’ command, so as mentioned in the previous task, I can download it with the ‘get’ command. 

Flag is 035db21c881520061c53e0536e44f815



#### 3. Dancing

Task 1

![htb](pictures/htbd1.png)

Task 2: What port does SMB use to operate at?

![htb](pictures/htbd2n3.png)

Ans: 445

Task 3: What is the service name for port 445 that came up in our Nmap  scan?

![htb](pictures/htbd2n3.png)

Ans: microsoft-ds?

Task 4: What is the 'flag' or 'switch' that we can use with the smbclient utility to 'list' the available shares on Dancing?

![htb](pictures/htbd4.png)

Ans: -L

Task 5: How many shares are there on Dancing?

![htb](pictures/htbd5.png)

Ans: 4

Task 6

![htb](pictures/htbd6.png)

WorkShares is the only share without  value under the comment column. 

Task 7

![htb](pictures/htbd7.png)

With the help command we can get all the applicable commands. I saw the ‘get’ command which is to download the files.

Task 8: Submit root flag

We can login to workshares as it doesn't require a password, so i login to workshare.
 
 ![htb](pictures/htbd8a.png)

After connecting to the workshares i found 2 folders so I checked them one by one. Inside the Amy.J folder there is a worknotes.txt which contains the text shown below:

![htb](pictures/htbdb.png)

Then I opened the James.P folder, inside the James.p folder there is a flag.txt file so I downloaded it and got the flag.

![htb](pictures/htbd8c.png)

Flag is 5f61c10dffbc77a704d76016a22f1664

![htb](pictures/htbdflag.png)
