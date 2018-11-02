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
• The computational capacity, limited by the CPUs
• The storage capacity, including the I/O transfer rate
• The network between the user and the centralized service

Size scalability problems for centralized services can be formally analyzed using queuing theory


**λ requests per second** processing capacity of the service is µ requests per second fraction

**Average throughput X** is equal to λ

**Utilization U** of a service as the fraction of time that it is busy

**Response time R:** how long does it take before the service to process a request, including the time spent in the queue

R = 1 / (1 - U)

**Geographical scalability:** Users and resources may lie far apart, but the fact that communication delays may be significant is hardly noticed.

Problems of Geographical scalability

1. Local-area networks based on Synchronous communication In this form of communication, a party requesting service, generally referred to as a client, blocks until a reply is sent back from the server implementing the service

2. Communication in wide-area networks is inherently much less reliable than in local-area networks.

3. Wide-area systems, we need to develop separate services, such as *naming* and *directory services* to which queries can be sent. These support services, in turn, need to be scalable as well and in many cases no obvious solutions exist as we will encounter in later chapters.

**Administrative scalability:** Easily managed even if it spans many independent administrative organizations. Conflicting policies with respect to resource usage (and payment), management, and security needs to be solved. For example, for many years scientists have been looking for solutions to share their (often expensive) equipment in what is known as a **computational grid**. In these grids, a global distributed system is constructed as a federation of local distributed systems, allowing a program running on a computer at organization A to directly access resources at organization B.

If a distributed system expands to another domain, two types of security measures need to be taken. 

- First, the distributed system has to protect itself against malicious attacks from the new domain. Only read access to the file system in its original domain. 

- Second, the new domain has to protect itself against malicious attacks from the distributed system. 

**Scaling techniques**

In DS, scalibility problems occur because of limited capacity of servers and network. 

1. Scaling up: Increasing memory, upgrading CPUs, or replacing network modules) 

2. Scaling out: Expanding the distributed system by essentially deploying more machines, there are basically only three techniques can be applied: 

    - Hiding communication latencies: applicable in the case of *geographical scalability*. Instead of waiting for a response in the server-side use *asynchronous communication*. In *interactive applications* asynchronous communication cannot be applied. If this is the case, moving part of the computation that is normally done at the server to the client process requesting the service, could be one improvement. 

<figure>
    <a href="/assets/images/PushCodeToClient.png"><img src="/assets/images/PushCodeToClient.png"></a>
</figure>

    - Distribution of work Partitioning and distribution: taking a component, splitting it into smaller parts, and subsequently spreading those parts across the system. Internet Domain Name System (DNS). The names in each zone are handled by a single name server. Tree of domains, nonoverlapping zones. *Naming service* is distributed accross machines. Second example is, World Wide Web is partitioned and distributed across a few hundred million servers. Only because of this distribution of documents that the Web has been capable of scaling to its current size.

<figure>
    <a href="/assets/images/DNS.png"><img src="/assets/images/DNS.png"></a>
</figure>

    - Replication: Balance the load between components leading to better performance. Geographically widely dispersed systems, having a copy nearby can hide much of the communication latency problems. **Caching** is a special form of replication. Caching is making a copy of a resource, in the proximity of the client accessing that resource. Unlike replication, caching is a decision made by the client of a resource. Caching and replication leads to **consistency**problems. 

Electronic stock exchanges and auctions, requires consistency. Replication requires global synchronization mechanism. 

**Pitfalls**

Peter Deutsch, at the time working at Sun Microsystems, formulated these ﬂaws as the following false assumptions that everyone makes when developing a distributed application for the first time:

• The network is reliable

• The network is secure

• The network is homogeneous

• The topology does not change

• Latency is zero

• Bandwidth is inﬁnite

• Transport cost is zero

• There is one administrator

**1.3 Types of distributed systems**

distributed computing systems, distributed information systems, and pervasive systems

**High performance distributed computing**

**Cluster computing** the underlying hardware consists of a collection of similar workstations or PCs, closely connected by means of a high-speed local-area network, each node runs the same operating system.

**Grid computing** This subgroup consists of distributed systems that are often constructed as a federation of computer systems, where each system may fall under a different administrative domain, and may be very different when it comes to hardware, software, and deployed network technology. Next step is to outsource entire infrastructure and this ends up in *cloud computing*.

**Note 1.8 (More information: Parallel processing)**

High-performance computing started with the introduction of multiprocessor machines. Multiple CPUs are organized in such a way that they all have access to the same physical memory. Multicomputer system several computers are connected through a network and there is no sharing of main memory. The shared-memory model proved to be highly convenient for improving the performance of programs and it was relatively easy to program. Distributed shared-memory multicomputers (DSM system). In essence, a DSM system allows a processor to address a memory location at another computer as if it were local memory

<figure>
    <a href="/assets/images/SharePrivateMemory.PNG"><img src="/assets/images/SharePrivateMemory.PNG"></a>
</figure>

**Cluster computing**

Became popular when price/performance ratio of personal computers and workstations improved. One of the feature of CC is its homogeneity, the computers in a cluster are largely the same, have the same operating system, and are all connected through the same network.

<figure>
    <a href="/assets/images/ClusterComputing.PNG"><img src="/assets/images/ClusterComputing.PNG"></a>
</figure>

**Grid computing**

<figure>
    <a href="/assets/images/GridComputing.PNG"><img src="/assets/images/GridComputing.PNG"></a>
</figure>

No assumptions are made concerning similarity of hardware, operating systems, networks, administrative domains, security policies. Virtual organization

<figure>
    <a href="/assets/images/LayeredArchitectureGridComputing.PNG"><img src="/assets/images/LayeredArchitectureGridComputing.PNG"></a>
</figure>

*Fabric layer:* Provides interfaces to local resources at a specific site.

*Connectivity layer:* Communication protocols for supporting grid transactions that span the usage of multiple resources.

*Resource layer:* Manages a single resource using the functions provided by the connectivity layer and calls directly the interfaces made available by the fabric layer.

*Collective layer:* Handling access to multiple resources and typically consists of services for resource discovery, allocation and scheduling of tasks onto multiple resources, data replication, and so on.

*Application layer:* Applications that operate within a virtual organization.

Service-oriented architecture - Open Grid Services Architecture (OGSA) 

**Cloud computing**

**Utility computing** by which a customer could upload tasks to a data center and be charged on a per-resource basis. Utility computing formed the basis for what is now called cloud computing. "Easily usable and accessible pool of virtualized resources". *Pay-per-use* model in which guarantees are offered by means of customized service level agreements (SLAs).

<figure>
    <a href="/assets/images/CluodComputing.PNG"><img src="/assets/images/CluodComputing.PNG"></a>
</figure>

Hardware: Manage the necessary hardware: processors, routers, but also power and cooling systems. Implemented at data centers and contains the resources that
customers normally never get to see directly. 

Infrastructure: Provide customers an infrastructure consisting of virtual storage and computing resources. 

Platform: Platform layer provides to a cloud-computing customer what an operating system provides to application developers, namely the means to easily develop and deploy applications that need to run in a cloud. Amazon S3 storage system is offered to theapplication developer in the form of an API allowing (locally created)
ﬁles to be organized and stored in buckets. 

Application: Actual applications run in this layer and are offered to users for further customization. (text processors, spreadsheet applications, presentation
applications, and so on). Applications are again executed in the vendor’s cloud. 

• Infrastructure-as-a-Service (IaaS) covering the hardware and infrastructure layer
• Platform-as-a-Service (PaaS) covering the platform layer
• Software-as-a-Service (SaaS) in which their applications are covered

Cloud computing has some serious obstacles like: provider lock-in, security and privacy issues, and dependency on the availability of service.

**Distributed information systems**

For networked applications, interoperability turned out to be a painful experience. Apps communicate with each other and provide services to remote apps called clients. Distributed transactions. This lead to Enterprise Application Integration (EAI).

**Distributed transaction processing**

Operations on a database are carried out in the form of *transactions*. Remote procedure calls(RPCs), that is, procedure calls to remote servers, are often also encapsulated in a transaction, leading to what is known as a transactional RPC.

Example primitives for transactions:

Primitive               |Description
BEGIN_TRANSACTION       |Mark the start of a transaction
END_TRANSACTION         |Terminate the transaction and try to commit
ABORT_TRANSACTION       |Kill the transaction and restore the old values
READ                    |Read data from a ﬁle, a table, or otherwise
WRITE                   |Write data to a ﬁle, a table, or otherwise

All-or-nothing property of transactions is also called ACID properties:

• **Atomic:** To the outside world, the transaction happens indivisibly
• **Consistent:** The transaction does not violate system invariants
• **Isolated:** Concurrent transactions do not interfere with each other
• **Durable:** Once a transaction commits, the changes are permanent

Number of subtransactions, jointly forming a nested transaction.

<figure>
    <a href="/assets/images/NestedTransaction.PNG"><img src="/assets/images/NestedTransaction.PNG"></a>
</figure>

The component that handled distributed (or nested) transactions formed the core for integrating applications at the server or database level. This component was called a
**transaction processing monitor** or **TP monitor** for short. TP monitor coordinated the commitment of subtransactions following a standard protocol known as **distributed commit**.

<figure>
    <a href="/assets/images/TPMonitor.PNG"><img src="/assets/images/TPMonitor.PNG"></a>
</figure>

**Enterprise application integration**

**Remote procedure calls (RPC)** an application component can effectively send a request to another application component by doing a local procedure call, which results in the request being packaged as a message and sent to the callee.

**Remote method invocations (RMI)** An RMI is essentially the same as an RPC, except that it operates on objects instead of functions.

<figure>
    <a href="/assets/images/MiddlewareCommunication.PNG"><img src="/assets/images/MiddlewareCommunication.PNG"></a>
</figure>

RPC and RMI have the disadvantage that the caller and callee both need to be up and running at the time of communication. This lead to message-oriented middleware, or simply MOM. 

**Publish/subscribe systems** applications send messages to logical contact points, often described by means of a subject, then applications can indicate their interest for a speciﬁc type of message, after which the communication middleware will take care that those messages are delivered to those applications.

**Note 1.10 (More information: On integrating applications)**










**Power usage effectiveness (PUE)** is a ratio that describes how efficiently a computer data center uses energy; specifically, how much energy is used by the computing equipment (in contrast to cooling and other overhead). PUE was originally developed by a consortium called The Green Grid. [2]

<figure>
    <a href="/assets/images/PUE.svg"><img src="/assets/images/PUE.svg"></a>
    <figcaption>Power Usage Efficiency Formula</figcaption>
</figure>


**References**

[1] Andrew S. Tanenbaum and Maarten van Steen. 2006. Distributed Systems: Principles and Paradigms (2nd Edition). Prentice-Hall, Inc., Upper Saddle River, NJ, USA.

[2] https://en.wikipedia.org/wiki/Power_usage_effectiveness