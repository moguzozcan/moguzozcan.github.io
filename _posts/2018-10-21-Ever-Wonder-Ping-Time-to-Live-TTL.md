---
title: "Ever Wonder Ping TTL Time-to-Live"
date: 2018-10-21
categories: 
  - Linux Command, Ping
---

Have you ever wonder what is the meaning of TTL, that occurs when you ping a website. If you never cared about them, let's briefly explain what it is.

<figure>
    <a href="/assets/images/PingTTL.png"><img src="/assets/images/PingTTL.png"></a>
</figure>

<figure>
    <figcaption>Ping TTL</figcaption>
</figure>

Lastly, in Distributed Systems and Cloud Computer lecture, my instructer mentioned about that. Then I made a research about it to learn more. Maybe I will not use it in my life again but it got my attention :) 

**According to [1]**

TTL (Time To Live) is a timer value included in packets sent over networks that tells the recipient how long to hold or use the packet before discarding and expiring the data (packet). TTL values are different for different Operating Systems. So, you can determine the OS based on the TTL value. 

As you can see from the output of the ping google.com, I got the TTL value as 57. This shows that, google is hosted in a machine where the default TTL value is probably 64 and it returned 57 which is close to 64 (TTL default value of Linux system). So, from this we can understand the *OS of the remote system*. 

**Wikipedia refers TTL as**

It is referred as *hop limit*, it limits the lifespan or lifetime of data in a computer or network. [2] Once that limit is elapsed, that packet is discarded from the network and it returns back to the originating node. TTL is used to prevent indefinite circulation of the packages in the network.

There are the default TTL values of different Operating Systems. The most common values are; 60, 64, 200 and 255 based on the system and the device. If you are curious about the values [1] shows some of them, and you can also search the net.


**References**

[1] https://subinsb.com/default-device-ttl-values/

[2] https://en.wikipedia.org/wiki/Time_to_live