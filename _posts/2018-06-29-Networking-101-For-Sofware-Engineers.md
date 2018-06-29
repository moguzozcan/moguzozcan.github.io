---
title: "Networking-101-For-Sofware-Engineers"
date: 2018-06-29
categories: 
  - Jekyll
---

The networking is always one of the hardest topic for the software engineers. There are too many jargon words around and the whole idea does not quite understandable. Here I'll explaine those jargon words from some of the sources on the net that I found valuable.


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


**Gateway and Bridge**
A gateway is a network node that connects two networks using different protocols together. While a bridge is used to join two similar types of networks, a gateway is used to join two dissimilar networks. [5]

The most common gateway is the router, which connects a LAN, which is a home or enterprise network to the outside world, internet. 

A network gateway joins two networks so the devices on one network can communicate with the devices on another network. Without gateways, you couldn't be able to access the internet, communicate and send data back and forth. A gateway can be implemented completely in software, hardware, or a combination of both. Because a network gateway by definition appears at the edge of a network, related capabilities such as firewalls and proxy servers tend to be integrated with it



After reading and learning some stuff the following question arises? Since the both is very similar to each other, what are the differences between switch and bridge?

**Switch vs. Bridge**
They are both Level 2 devices
A bridge looks at the destination of the frame before sending, if the destination address is not on the other side of the bridge it will not transmit the data across. This helps break up one large broadcast domain into 2 by using one bridge device.

 

A switch has multiple ports in which each port is its own collision domain, a switch will determine the source and destination of the incoming data and switch it to the port it needs to go to. Switch ports can be broken into many separate broadcast domains using vlans. A switch is more efficient in today's large networks.


A bridge make its decision in software (done by the Main Processor) and a switch make is decision in hardware.

Bridge...Design to connect multiple network

Switch...Design to connect End devices




**References**

[1] https://www.youtube.com/watch?v=6_FHs_g1yw4 - Networking 101 for Software Engineers – Gabriel Rosenhouse

[2] https://www.youtube.com/watch?v=aQVuZKLtBJg - Chapter 1 - Tutorial Basics NETWORK - Fundamental of Personal Computer

[3] https://www.youtube.com/watch?v=1z0ULvg_pW8 - Hub, Switch, & Router Explained - What's the difference?

[4] https://www.youtube.com/watch?v=mpQZVYPuDGU - How DNS Works?

[5] https://internetofthingsagenda.techtarget.com/definition/gateway 