---
title: "Networking-101-For-Sofware-Engineers"
date: 2018-06-29
categories: 
  - Jekyll
---

The networking is always one of the hardest topic for the software engineers. There are too many jargon words around and the whole idea does not quite understandable. Here I'll explaine those jargon words from some of the sources on the net that I found valuable. This post will be mix of the all questions that I have in my mind and I found them by googling. I hope this posts helps some people who are struggling with networking. 

Firstly, why we need networking? This is the first question we had. There are PC's, Servers, Printer and many other devices out there needs communication. Therefore, we need to connect them and communicate over them. 

**Local Area Network (LAN) vs. Wide Area Network (WAN)**

Both LAN and WAN allows interconnectivity between computers. 

LAN as the name suggest stands for local networks like home, business or school. LAN's are faster and more secure than WAN. LANs are controlled and managed by some in-house organization or people. 

WAN covers larger areas, like cities, nations etc. WAN requires two or more LAN to be connected over internet or some connection. The Internet is an example of a worldwide public WAN.

There is also MAN (metropolitan area network) which is a larger network that usually spans several buildings in the same city or town. The IUB network is an example of a MAN. But, personally, I do not think this term is so important. 

[7]



Layers:
There are two models:

**OSI Layer** Developed by telecommunications industry 7 Layers, Numbered

**TCP/IP** Developed by US and UK military 4 layers, Named

Layer 1: Physical - Message is bits, the medium is voltages or radio waves

Layer 2: Data Link - In this layer, the bits in layer 1 gets some meaning. The thing called "Ethernet Frame" is created by ordering the bits. There is also a thing called packet, which is actually:
Packet = Header + Frame + Footer







**Hub:**
Connect devices in internal network, not intelligent. When data packet is arrived in a hub, it copies that packet to all ports.
Not secure, and unnecessary network, bandwidth.[3]

**Switch:**
Similar to hub, connect devices in port, intelligent, learn addresses of devices, stores physical address (MAC addresses) When data
arrives, it in directed to intended port. Swith preferred over hub, eliminates unnecessary network. [3]

**Router:**
Hub and Swithes are used to exchange data in a local area network(LAN), not outside it.  For that, a device need to read IP addresses. 
Router, as the name implies routes or forwards a data packet wrt it's IP address. Determines if the data is meant for it's own network or another network. If data is for the router, it receives the data, if not it sends the data to another network. It is basically a gateway. [3]

**TL;DR** Hubs & Switches are used to create networks, whereas the Routers are used to connect networks. [3]


**Domain Name System DNS**
Resolves names to IP addresses. Basically works like a phonebook. [4]
Steps of DNS
1. If browser or OS can't find IP in cache memory send request to Resolver Server(ISP - Internet Service Provider)
2. Resolver checks it's cache to find the IP of the given name, if it can't finds it, it direct query to Root Server.
3. Top or the Root of the DNS hierarchy, 13 sets of Root servers placed around the world and operated by 12 different organizations. Each set has their own unique IP addresses. If Root server can't find the query.
4. Directs Resolver to TLD (Top Level Domain Server) .com domain. yahoo.com.
5. TLD stores the address information for the top level domains, such as .com, .net, .org etc.
6. TLD direct resolver to Authorative Name Server.
7. Resolver ask ANS the IP of yahoo.com, ANS is responsible for knowing everything about the domain. Final authority. 
8. Resolver stores IP address in it's cache in case of the future queries to avoid going through all those steps over again. 




**DHCP Server**
Another term that is heard a lot in the network domain is DHCP Server. DHCP stands for Dynamic Host Configuration Protocol. It is used to provide automatic and fast ip distribution in a network. It is also the central management for this task. If there would not be a DHCP server, all the clients need to configure network parameters by themselves. DHCP also configures the subnet mask, default gateway and DNS server. 

Mostly, routers act as DHCP servers, but in some cases generally in big networks a dedicated computer might be used as a DHCP server. The process of getting an IP from a DHCP server for a device is as follows:

1. Device sends DHCPDISCOVER request to server

2. Server responds DHCPOFFER packet with the necessary information inside

3. Device sends DHCPREQUEST packet to accept the offer

4. Finally DHCPserver sends ACK (or NACK) to confirm (or not) device has that IP.


**Pros and Cons of DHCP Server:**

- Get rid of burden of setting network configurations manually.
 
- Decrease change of getting same IP addresses for two devices.

- There is also a burden of unassigning the IP address if setted manually before.

- There can be a need for static IP settings which is done manually, like printers 



**What is subnet mask?**
Basically, subnet mask divides the IP address into two parts, the network address and the host address. This way, the network becomes more manageable in terms of the floating traffic. For example, let's assume there will be a communication between two devices with the following IP addresses. 192.168.1.1 to 192.168.1.200. If the subnet mask of these two devices are 255.255.255.0, this means that they are in the same network. The 255's in the subnet mask defines the address of the network, which the same for all the devices that are in the same subnet. In the previous example, subnet mask was 255.255.255.0, in this case "192.168.1" is the address of the network, and the last octet is address of the host. If subnet mask would be 255.255.0.0 then "192.168" would be address of the network and the last two octet would be the address of the host. 

What is the difference if two devices are in the same subnet mask?

If two devices are in the same subnet mask, the communication between them is done by the broadcast. Broadcast sends the messages that arises from one device to all the devices in the network. If the subnet is larger the occurred traffic will consume more network. 

**What is default gateway?**
The default IP address is the private IP address assigned to the router that the network uses. 

**What is a DNS Server?**



**Gateway and Bridge**
A gateway is a network node that connects two networks using different protocols together. While a bridge is used to join two similar types of networks, a gateway is used to join two dissimilar networks. [5]

The most common gateway is the router, which connects a LAN, which is a home or enterprise network to the outside world, internet. 

A network gateway joins two networks so the devices on one network can communicate with the devices on another network. Without gateways, you couldn't be able to access the internet, communicate and send data back and forth. A gateway can be implemented completely in software, hardware, or a combination of both. Because a network gateway by definition appears at the edge of a network, related capabilities such as firewalls and proxy servers tend to be integrated with it



After reading and learning some stuff the following question arises? Since the both is very similar to each other, what are the differences between switch and bridge?

**Switch vs. Bridge**
They are both Level 2 devices. A bridge looks at the destination of the frame before sending, if the destination address is not on the other side of the bridge it will not transmit the data across. This helps break up one large broadcast domain into 2 by using one bridge device. A bridge make its decision in software (done by the Main Processor) and a switch make is decision in hardware. Bridge is designed to connect multiple networks.

A switch has multiple ports in which each port is its own collision domain, a switch will determine the source and destination of the incoming data and switch it to the port it needs to go to. Switch ports can be broken into many separate broadcast domains using vlans. A switch is more efficient in today's large networks. Switch is designed to connect end devices. [6]


**References**

[1] https://www.youtube.com/watch?v=6_FHs_g1yw4 - Networking 101 for Software Engineers – Gabriel Rosenhouse

[2] https://www.youtube.com/watch?v=aQVuZKLtBJg - Chapter 1 - Tutorial Basics NETWORK - Fundamental of Personal Computer

[3] https://www.youtube.com/watch?v=1z0ULvg_pW8 - Hub, Switch, & Router Explained - What's the difference?

[4] https://www.youtube.com/watch?v=mpQZVYPuDGU - How DNS Works?

[5] https://internetofthingsagenda.techtarget.com/definition/gateway 

[6] https://learningnetwork.cisco.com/thread/41392

[7] https://www.diffen.com/difference/LAN_vs_WAN