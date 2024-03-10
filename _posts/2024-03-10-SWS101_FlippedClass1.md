---
Title: SWS101 Flipped Class 1
categories: [SWS101, Flipped_class1]
tags: [SWS101]
---

## Topic: Networking 
Computer networking refers to connecting computers and other devices to share resources and information.

### Networking Devices
- Router: Connects different networks together.
- Switch: Connects devices within a local network.
- Hub: Connects multiple devices in a LAN but operates at the physical layer.
- Modem: Converts digital data from a computer into signals suitable for transmission over communication lines.

### Topology
Topology refers to the way computers are arranged and connected to each other. It defines how data flows within the network.

### Network topologies
* Point-to-Point
* Star
* Mesh
* Hybrid
* Bus
* Ring
* Tree
* Daisy Chain

### Network Types
Wan(wide area network) 
Network that covers a large area and it is commonly referred to as the internet.

Lan(Local area network)
Network that covers a limited area such as home, school, college, etc. It is a internal network.

wlan(wireless local area network)
Type of local area network that uses wifi over wire. It is an internal network over wifi.

Vpn(virtual private network)
Vpn allows connecting multiple network sides to one lan. There are three main types of vpn :
- site-to-site vpn
- remote access vpn
- ssl vpn

### Proxy
A proxy is when a device or service sits in the middle of a connection and acts as a mediator.Without the ability to be a mediator, the device is technically a gateway, not a proxy.
Key proxies:
- Dedicated Proxy / Forward Proxy
- Reverse Proxy
- Transparent Proxy

### Networking model
The OSI (Open Systems Interconnection) Model and the TCP/IP (Transmission Control Protocol/Internet Protocol) Model are two common networking models that define the functions of a communication system.

### OSI model(Open Systems Interconnection)
The OSI Model is a conceptual model that standardizes the functions of a communication or computing system into seven abstraction layers.

![osi](pictures/osiModel.png)

Seven Layers from bottom to top:
1. Physical layer
Concerned with the physical connection between devices.eg Ethernet cables, USB, Bluetooth.

2. Data-link layer
Responsible for creating a reliable link between two directly connected nodes.eg switch, bridge.

3. Network layer
Focuses on routing and forwarding data packets between devices across different networks.eg router, L3 switch.

4. Transport layer
Ensures end-to-end communication, providing error recovery and flow control. Eg TCP (Transmission Control Protocol), UDP (User Datagram Protocol).

5. Session layer
Manages sessions or connections between applications. eg NetBIOS (Network Basic Input/Output System).

6. Presentation layer
Translates data between the application layer and the lower layers. Eg JPG, PNG, SSL, TLS. 

7. Application layer
Represents the user interface and provides network services directly to applications. Eg FTP, HTTP, DNS.

### Network Protocol
It is a set of rules that define how data is transmitted over a network. Protocol is like a common language that computers use to communicate with each other.

### TCP/IP (Transmission Control Protocol/Internet Protocol)
The protocols are responsible for the switching and transport of data packets on the Internet.
The Internet is entirely based on the TCP/IP protocol family.
However, TCP/IP does not only refer to these two protocols but is usually used as a generic term for an entire protocol family.

It consists of four layers: 
1. Link
Concerned with the physical connection between devices and the framing, addressing, and access control for the network medium.

2. Internet
Responsible for logical addressing, routing, and the fragmentation and reassembly of packets.

3. Transport
Equivalent to the Transport layer in the OSI model.

4. Application
Facilitates communication between software applications and the network.

![TCP](pictures/tcpModel.png)

** Note that ** 
The OSI (Open Systems Interconnection) model and the TCP/IP (Transmission Control Protocol/Internet Protocol) model, although developed independently, can be loosely mapped to each other.

Link layer from the TCP/IP model is equivalent to the combination of the Physical and Data Link layers in the OSI model.

Network layer corresponds to the internet layer in the TCP/IP model. Transport layer corresponds to the Transport layer in the TCP/IP model.

Application layer from the TCP/IP model is equivalent to the combination of the Session, Presentation, and Application layers in the OSI model. The diagram below sum up my point;

![Both](pictures/both.png)

### Packet transfer
Packet transfer is the process by which data is broken down into smaller units called packets and transmitted across a network from a source to a destination.

In a layered system, devices in a layer exchange data in a different format called a protocol data unit (PDU).

### Network layer
The network layer uses logical addressing (e.g. IP addresses) to uniquely identify devices on a network.

#### IPv4 vs IPv6
![IPv4](pictures/ipv4-vs-ipv6.png)

#### Subnetting 
Subnetting is a networking technique that involves dividing an address range of IPv4 addresses into several smaller address ranges.

#### MAc addresses
A MAC (Media Access Control) address is a unique identifier assigned to network interfaces for communication on a physical network.

Each host in a network has its own 48-bit (6 octets) Media Access Control (MAC) address, represented in hexadecimal format.

### TCP 3-Way Handshake
In the establishment of a TCP connection between a client and a server, a TCP three-way handshake process is performed.The three-way handshake is a fundamental process in establishing a reliable communication connection using the Transmission Control Protocol (TCP). It ensures that both the sender and receiver are ready for data exchange

![3way](pictures/3way.png)

To understand the three way handshake better, let's imagine Karma and Tshering want to exchange secret messages, and Karma wants to make sure the messages are delivered reliably. 

1. Hello Tshering (SYN):
- You send a message to your friend saying, "Hello Tshering, I want to talk to you." This is like the first step, called "SYN" in computer terms which stands for synchronize. It's your way of saying, "Let's start talking."

2. Reply from Tshering (SYN-ACK):
- Tshering receives Karma’s message and responds, "Sure, I got your message, and I'm ready to talk too." This is the second step, known as "SYN-ACK." It's like Tshering is acknowledging Karma’s request and saying, "Let's have a conversation."

3. Okay, Let's Talk (ACK):
- Karma then replies back to Tshering, saying, "Great! Let's start our conversation." This is the final step, called "ACK" (acknowledge). It's KArma’s way of confirming that he got your friend's response and that you're both ready to exchange secret messages.

### Wireless network
Wireless networks are computer networks that use wireless data connections between network nodes/hosts.

To connect to a wireless network, a device must be within range of the network and configured with the correct network settings, such as the network name and password.

Wireless networks use radio frequency (RF) technology to transmit data between devices.

### VPN
A Virtual Private Network (VPN) is a technology that allows a secure and encrypted connection between a private network and a remote device. 

### IPsec
Internet Protocol Security (IPsec) is a network security protocol that provides encryption and authentication for internet communications.

### PPTP
point-to-Point Tunneling Protocol (PPTP) is also a network protocol that allows the creation of VPNs and works by establishing a secure tunnel between the VPN client and server and then encapsulating the data being transmitted within this tunnel. 







