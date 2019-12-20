---
title: "CAP Theorem"
date: 2018-10-15
categories: 
  - Distibuted Systems
  - CAP Theorem
---

Lately, I came accross with the CAP Theorem a few times so I want to read and learn about it. CAP states for Consistency, Availability, and Partition Tolerance and this theorem states that in a distributed system, these three cannot exist in the same time. At least one of them has to be sacrificied to have the others. Let's explain them one by one to understand the reasoning. The [2] is one of the best resource that explains this in plain English. 

**Consistency**

In a DS, an update is made in one of the nodes of the system and then a get request is made and if this get request is directed to another node in the system, the request should return the latest information and all of the nodes should be aware of the latest updates and they all should return the same response.

**Availability** 

The system should return to any call without any errors.

**Partition Tolerance**

Partition means something that is divided or separate or divide something. If the connection between the node is lost, the system should work without affecting. In this case partition means if the true data is divided between nodes, they should return the correct information.

<figure>
    <a href="/assets/images/cap_theorem.jpeg"><img src="/assets/images/cap_theorem.jpeg"></a>
    <figcaption>VENN Diagram of the CAP Theorem</figcaption>
</figure>

**Wikipedia explanation**

CAP theorem is found by computer scientist Eric Brewer at 2000 and theorem is also named Brewer's theorem after. Theorem states that it is impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees:

**Consistency:** Every read receives the most recent write or an error

**Availability:** Every request receives a response that is not an error

**Partition tolerance:** The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes

In particular, the CAP theorem implies that in the presence of a network partition, one has to choose between consistency and availability. Note that consistency as defined in the CAP theorem is quite different from the consistency guaranteed in ACID database transactions. [3]


**Run Around Clerk** 

Clerk means writer, recorder or office worker. Eventual consistency can be provided with a run around clerk. This is a backgroud task that works to update the nodes without affecting their work and provides synchronization of the all nodes. Many NoSQL systems are working like that. However, for a small period of time consistency may not be provided. But, if there is too less time between an update and a select or get request. 

**References**

[1] https://www.interviewbit.com/tutorial/cap-theorem/#cap-theorem

[2] http://ksat.me/a-plain-english-introduction-to-cap-theorem/

[3] https://en.wikipedia.org/wiki/CAP_theorem