---
Title: SWS101 Flipped Class 4
categories: [SWS101, Flipped_class4]
tags: [SWS101]
---

# Topic: Traffic Analysis Essentials

![traffic](/pictures/SWS_pictures/traffic.png)

## Introduction
Network Security is a set of operations for protecting data, applications, devices and systems connected to the network. It is accepted as one of the significant subdomains of cyber security. It focuses on the system design, operation and management of the architecture/infrastructure to provide network accessibility, integrity, continuity and reliability. Traffic analysis (often called Network Traffic Analysis) is a subdomain of the Network Security domain, and its primary focus is investigating the network data to identify problems and anomalies.

## Network Security
![net](/pictures/SWS_pictures/networkdata.png)

Network security operations contain three base control levels to ensure the maximum available security management.

![net](/pictures/SWS_pictures/networklevel.png)

There are two main approaches and multiple elements under these control levels.

![net](/pictures/SWS_pictures/mainapproach.png)

The two common key elements of Threat Controls are <b>Security Information and Event Management (SIEM)</b> and <b>Security Orchestration Automation and Response (SOAR).</b>

### Security Information and Event Management (SIEM)
Most systems produce logs often containing important security information. An event is simply observations we can determine from logs and information from the network, for example:
- Users logging in
- Attacks observed in the network
- Transactions within applications

The SIEM processes alerts based on logs from different sensors and monitors in the network, each which might produce alerts that are important for the SOC to respond to. The SIEM can also try to correlate multiple events to determine alerts.

SIEM's typically allow events from the following areas to be analyzed:
- Network
- Host
- Applications

Events from the network are the most typical, but least valuable as they don't hold the entire context of what has happened. The network typically reveals who is communicating where, over which protocols, and when, but not the intricate details about what happened, to whom and why.

Host events give more information in regards to what actually happened and to whom. Challenges such as encryption are no longer blurred and more visibility is gained into what is taking place. Many SIEM's are enriched with great details about what happens on the hosts themselves, instead of only from the network.

Events from application are where the SOC typically can best understand what is going on. These events give information about the Triple A, AAA ("Authentication, Authorization and Account"), including detailed information about how the application is performing and what the users are doing.


### Security Orchestration Automation and Response (SOAR)
To counter the advancements of threat actors, automation is key for a modern SOC to respond fast enough. To facilitate fast response to incidents, the SOC should have tools available to automatically orchestrate solutions to respond to threats in the environment.

The SOAR strategy means ensuring the SOC can use actionable data to help mitigate and stop threats which are developing more real-time than before. In traditional environments it takes attackers a very short time from the time of compromise until they have spread to neighboring systems. Contrary to this it takes organizations typically a very long time to detect threats that have entered their environment. SOAR tries to help solve this.

SOAR includes concepts such as IAC "Infrastructure as Code" to help rebuild and remediate threats. SDN ("Software Defined Networking") to control accesses more fluently and easily, and much more.

The picture below is the questions and answers from the network security part.
![net](/pictures/SWS_pictures/QnA.png)

## Traffic Analysis
![net](/pictures/SWS_pictures/trafficanalysis.png)

Traffic Analysis is a method of intercepting, recording/monitoring, and analyzing network data and communication patterns to detect and respond to system health issues, network anomalies, and threats. The network is a rich data source, so traffic analysis is useful for security and operational matters. The operational issues cover system availability checks and measuring performance, and the security issues cover anomaly and suspicious activity detection on the network.

There are two main techniques used in Traffic Analysis:

![net](/pictures/SWS_pictures/flow.png)

Benefits of the Traffic Analysis:
- Provides full network visibility.
- Helps comprehensive baselining for asset tracking.
- Helps to detect/respond to anomalies and threats.

Answer the questions below:
At the top of the task, click the green View Site button.

![net](/pictures/SWS_pictures/viewsite.png)

The screen will split, and we are  ready to start.

![net](/pictures/SWS_pictures/Netsec.png)

Level-1 is simulating the identification and filtering of malicious IP addresses.
What is the flag?
Click the black Start Network Traffic button.

![net](/pictures/SWS_pictures/restorerun.png)

We will see traffic running across the network, but unfortunately we got malware. So, click this  black button labeled Restore the Network and record the traffic for further investigation.

![net](/pictures/SWS_pictures/log.png)

Now we are instructed to find 2 IP addresses for the firewall to filter. Looking through the IDS/IPS system, we can see a couple of suspicious IP addresses. Among them, Multiple Login Attempts, bad traffic and metasploit traffic are the most suspicious ones. For now let's add the ip address of Multiple Login Attempts and bad traffic since Multiple Login Attempts and metasploit traffic has same ip address.

![net](/pictures/SWS_pictures/level1flag.png)

Boom we got our flag for level 1. Now let's go to level 2.

![net](/pictures/SWS_pictures/level2.png)

Now instead of an ip address, we are instructed to add 3 port numbers. As we know the 3 suspicious machines add their port number. I.e is 4444, 7777, 2222

![net](/pictures/SWS_pictures/level2flag.png)

Boom we got a flag for level 2 also.

## Conclusion
From this Traffic Analysis Essentials room, I learned the foundations of the network security and traffic analysis concepts:
- Network Security Operations
- Network Traffic Analysis

Network security operations encompass the ongoing efforts to safeguard a network's infrastructure, while network traffic analysis plays a vital role in identifying and mitigating potential security risks by monitoring and analyzing data traffic.
