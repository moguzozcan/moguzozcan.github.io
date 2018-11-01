---
title: "Distributed Systems Lecture and Book Notes"
date: 2018-11-01
categories: 
  - Distributed Systems, Book Notes
---

**Introduction**

Two development cause the rise of distributed systems:

1. Development of powerful microprocessors. Initially, these were 8-bit machines, but soon 16-, 32-, and 64-bit CPUs became common. Then, multicore CPUs.

2. Invention of high-speed computer networks.

**Local-area networks (LAN)**: Machines within a building to be connected.
**Wide-area networks (WAN)**: Hundreds of millions of machines all over the earth to be connected at speeds varying from tens of thousands to hundreds of millions bps.

**1.1 What is a distributed system?**

A distributed system is a collection of autonomous computing elements that appears to its users as a single coherent system.

Two characteristics of DS:

1. A collection of computing elements **(node)** each being able to behave independently of each other.

    **Group membership**
    **Open group:** Any node is allowed to join the distributed system, effectively meaning that it can send messages to any other node in the system. 
    **Closed group:** Only the members of that group can communicate with each other and a separate mechanism is needed to let a node join or leave the group

    Practice shows that a distributed system is often organized as an **overlay network** (Örtü, yerleşim ağı in Turkish)

    **Structured overlay:** In this case, each node has a well-deﬁned set of neighbors with whom it can communicate. For example, the nodes are organized in a tree or logical ring.

    **Unstructured overlay:** In these overlays, each node has a number of references to randomly selected other nodes.

    Overlay networks are always connected. They form **peer-to-peer (P2P) networks**

2. Users believe they are dealing with a single system.

    User would not be able to tell exactly on which computer a process is currently executing, or even perhaps that part of a task has been spawned off to another process executing somewhere else. Likewise, where data is stored should be of no concern, and neither should it matter that the system may be replicating data to enhance performance. This so called **distribution transparency**

**Middleware and distributed systems**

Middleware: DS are often organized to have a separate layer of software that is logically placed on top of the respective operating systems of the computers that are part of the system.

<figure>
    <a href="/assets/images/MiddlewareAndDS.PNG"><img src="/assets/images/MiddlewareAndDS.PNG"></a>
</figure>

In a sense, middleware is the same to a distributed system as what an operating system is to a computer: a manager of resources offering its applications to efficiently share and deploy those resources across a network. Next to resource management, it offers services that can also be found in most operating systems, including:

• Facilities for interapplication communication.
• Security services.
• Accounting services.
• Masking of and recovery from failures.

**Typical middleware services**

**Communication:** Remote Procedure Call (RPC). allows an application to invoke a function that is implemented and executed on a remote computer as if it was locally available. 

**Transactions:** Executing services in an all-or-nothing fashion, referred to as an atomic transaction, the middleware makes sure that every service is invoked, or none at all.

**Service composition:** It is becoming increasingly common to develop new applications by taking existing programs and gluing them together. This is notably the case for many Web-based applications, in particular those known as **Web services** [Alonso et al., 2004]. Web-based middleware can help by standardizing the way Web services are accessed and providing the means to generate their functions in a speciﬁc order. A simple example of how service composition is deployed is formed by mashups:
Web pages that combine and aggregate data from different sources. Well-known mashups are those based on **Google maps** in which maps are enhanced with extra information such as trip planners or real-time weather forecasts.

**Reliability:** The Horus toolkit [van Renesse et al., 1994] allows a developer to build an application as a group of processes such that any message sent by one process is guaranteed to be received by all or no other process. As it turns out, such guarantees can greatly simplify developing distributed applications and are typically implemented as part of the middleware.

**1.2 Design goals**

Resources can be virtually anything, peripherals (çevre birimler), storage facilities, data, ﬁles, services, and networks. Making distribution transparent is one aim of DS.

**Types of distribution transparency**

*Transparency*          |*Description*
Access                  |Hide differences in data representation and how an object is accessed
Location                |Hide where an object is located
Relocation              |Hide that an object may be moved to another location while in use
Migration               |Hide that an object may move to another location
Replication             |Hide that an object is replicated
Concurrency             |Hide that an object may be shared by several independent users
Failure                 |Hide the failure and recovery of an object












**References**

[1] Andrew S. Tanenbaum and Maarten van Steen. 2006. Distributed Systems: Principles and Paradigms (2nd Edition). Prentice-Hall, Inc., Upper Saddle River, NJ, USA.