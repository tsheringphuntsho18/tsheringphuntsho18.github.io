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

#### Meow
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

