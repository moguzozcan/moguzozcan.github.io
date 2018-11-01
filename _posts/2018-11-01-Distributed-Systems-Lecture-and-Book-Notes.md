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

Goals of DS:

1. Supporting resource sharing
2. Making distribution transparent
3. Being open
4. Being scalable

**Supporting resource sharing**
Resources can be virtually anything, peripherals (çevre birimler), storage facilities, data, ﬁles, services, and networks. Making distribution transparent is one aim of DS.

**Making distribution transparent**
**Types of distribution transparency**

*Transparency*          |*Description*
Access                  |Hide differences in data representation and how an object is accessed
Location                |Hide where an object is located
Relocation              |Hide that an object may be moved to another location while in use
Migration               |Hide that an object may move to another location
Replication             |Hide that an object is replicated
Concurrency             |Hide that an object may be shared by several independent users
Failure                 |Hide the failure and recovery of an object

**Access transparency**

Hiding differences in data representation and the way that objects can be accessed. Different OS and naming conventions, file operations or low-level communication with other processes must be hidden from user and apps. 

**Location transparency**

Users cannot tell where an object is physically located in the system. Achieved by assigning only logical names to resources, that is, names in which the location of a resource is not secretly encoded. Uniform resource locator (URL) http://www.prenhall.com/index.html, which gives no clue about the actual location of Prentice Hall’s main Web server

**Relocation transparency**

If the entire site may have been moved from one data center to another, users should not notice. This is becoming increasingly important in the context of cloud computing.

**Migration transparency**

Supports the mobility of processes and resources initiated by users, without affecting ongoing communication and operations. Communication between mobile phones, regardless whether two people are actually moving, mobile phones will allow them to continue their conversation. Online tracking and tracing of goods as they are being transported from one place to another, and teleconferencing (partly) using devices that are equipped with mobile Internet.

**Replication transparency**

Resources may be replicated to increase availability or to improve performance by placing a copy close to the place where it is accessed. Hiding the fact that several copies of a resource exist, or that several processes are operating in some form of lockstep mode so that one can take over when another fails. All replicas have the same name. A system that supports replication transparency should generally support location transparency as well.

**Concurrency transparency**

Two independent users may each have stored their ﬁles on the same file server or may be accessing the same tables in a shared database and each user does not notice that the other is making use of the same resource.

**Failure transparency**

A user or application does not notice that some piece of the system fails to work properly, and that the system subsequently (and automatically) recovers from that failure.

**Being Open**

A system that offers components that can easily be used by, or integrated into other systems. At the same time, an open distributed system itself will often consist of components that originate from elsewhere.

**Interoperability, composability, and extensibility**

Deﬁne services through interfaces using an **Interface Deﬁnition Language (IDL)**

**Interoperability** characterizes the extent by which two implementations of systems or components from different manufacturers can co-exist and work together by merely relying on each other’s services as speciﬁed by a common standard

**Portability** characterizes to what extent an application developed for a distributed system A can be executed, without modiﬁcation, on a different distributed system B
that implements the same interfaces as A. 

**Extensible** easy to add new components or replace existing ones without affecting those components that stay in place. An open distributed system should also be extensible. Easy to add parts that run on a different operating system, or even to replace an entire file system

**Separating policy from mechanism**

System be organized as a collection of relatively small and easily replaceable or adaptable components. Monolithic approach, the older way of development does not provide this.

**Caching in Web browsers**

Need to consider, Storage, Exemption, Sharing and Refreshing topics. Need to offer a rich set of parameters that the user can set (dynamically).

Trade-off: Strict separation of policies and mechanisms may lead to *highly complex conﬁguration* problems. To solve this, provide reasonable defaults. Self-conﬁgurable systems.

**Being scalable**

**Size scalability:** Easily add more users and resources to the system without any noticeable loss of performance.

**Geographical scalability:** Users and resources may lie far apart, but the fact that communication delays may be significant is hardly noticed.

**Administrative scalability:** Easily managed even if it spans many independent administrative organizations.


























**Power usage effectiveness (PUE)** is a ratio that describes how efficiently a computer data center uses energy; specifically, how much energy is used by the computing equipment (in contrast to cooling and other overhead). PUE was originally developed by a consortium called The Green Grid. [2]

<figure>
    <a href="/assets/images/PUE.svg"><img src="/assets/images/PUE.svg"></a>
    <figcaption>Power Usage Efficiency Formula</figcaption>
</figure>




**References**

[1] Andrew S. Tanenbaum and Maarten van Steen. 2006. Distributed Systems: Principles and Paradigms (2nd Edition). Prentice-Hall, Inc., Upper Saddle River, NJ, USA.

[2] https://en.wikipedia.org/wiki/Power_usage_effectiveness