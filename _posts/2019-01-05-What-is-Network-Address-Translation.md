---
title: "What is Network Address Translation"
date: 2018-01-05
categories: 
  - Network Address Translation
  - NAT
---

I made a list named "post topics", where I am storing the topics that I would like to first learn and then share with you. Since I am in a PhD break, I will focus more on the writing and coding. The topic of today is **NAT**, Network Address Translation. I've heard about it many times, but I never exactly know it's details and what it is doing, why it is used etc. Let's dive deep and learn!

NAT is basically converting one IP address to another by changing the information in the packet header. **[2]** The need occurred because of the IPv4 address exhaustion. The current IP addresses (IPv4) in the world are limited, which is 2 to 32 bit 4,294,967,296 addresses. However, since large blocks of IPv4 addresses are reserved for special uses and are unavailable for public allocation, the actual limit is around 3 billion IP addresses. **[1]**, **[3]**. Therefore, it is not logical to give a public IP to all the devices in the world. Generally, the devices are connected to the internet via a router. Router provides the public IP address for the devices. Think about your home or a company, where there are many devices connected to the internet via the same router. Therefore, to save some space, private IP addresses are provided to each of the devices, where the private ip generally starts with 192.168.0.* or 192.168.1.*, and all the devices use only one public IP for the outside world.

The IP packets have source and destination IP addresses and shown in below figure. When a packet is going from private network to the public network, it's source address is changed to the public IP address of the network, and the private IP where the communication is initiated is stored in a table called "NAT Translation Table" to be able to redirect the packet to the originating device. This the the important functionality of the NAT to avoid ambiguity in the packets originated from the same public IP address. 

<figure>
    <a href="/assets/images/TCPPacket.jpg"><img src="/assets/images/TCPPacket.jpg"></a>
    <figcaption>TCP / IP packet header and body</figcaption>
</figure>

The two common protocols used today are Transmission Control Protocol (TCP) or User Datagram Protocol (UDP). A sample TCP packet is shown above. These protocols also store the port numbers for the source and destination. To avoid the ambiguity one more step is taken, which the source and destination ports are also change while the packet is transferred from one side to another. This is referred as **Port Address Translation (PAT)** in RFC 2663. **Network address and port translation (NAPT)**, **IP masquerading**, **NAT overload** and **many-to-one NAT** are another names used for this type of translation. 

A very short but detailed enough explanation of the NAT is explained. I hope it helps others as well!


**References**

**[1]** https://medium.com/@gokhansengun/nat-network-address-translation-nedir-ve-nas%C4%B1l-%C3%A7al%C4%B1%C5%9F%C4%B1r-a2c8b6291de8

**[2]** https://en.wikipedia.org/wiki/Network_address_translation

**[3]** https://en.wikipedia.org/wiki/IPv4_address_exhaustion