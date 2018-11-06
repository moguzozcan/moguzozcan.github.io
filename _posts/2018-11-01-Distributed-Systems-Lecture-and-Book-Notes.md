---
title: "Distributed Systems Lecture and Book Notes"
date: 2018-11-01
categories: 
  - Distributed Systems, Book Notes
---

# Chapter 1 Introduction #

Two development cause the rise of distributed systems:

1. Development of powerful microprocessors. Initially, these were 8-bit machines, but soon 16-, 32-, and 64-bit CPUs became common. Then, multicore CPUs.

2. Invention of high-speed computer networks.

**Local-area networks (LAN)**: Machines within a building to be connected.

**Wide-area networks (WAN)**: Hundreds of millions of machines all over the earth to be connected at speeds varying from tens of thousands to hundreds of millions bps.

## 1.1 What is a distributed system? ##

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

### Middleware and distributed systems ###

Middleware: DS are often organized to have a separate layer of software that is logically placed on top of the respective operating systems of the computers that are part of the system.

<figure>
    <a href="/assets/images/MiddlewareAndDS.PNG"><img src="/assets/images/MiddlewareAndDS.PNG"></a>
</figure>

In a sense, middleware is the same to a distributed system as what an operating system is to a computer: a manager of resources offering its applications to efficiently share and deploy those resources across a network. Next to resource management, it offers services that can also be found in most operating systems, including:

• Facilities for interapplication communication.

• Security services.

• Accounting services.

• Masking of and recovery from failures.

### Typical middleware services ###

**Communication:** Remote Procedure Call (RPC). allows an application to invoke a function that is implemented and executed on a remote computer as if it was locally available. 

**Transactions:** Executing services in an all-or-nothing fashion, referred to as an atomic transaction, the middleware makes sure that every service is invoked, or none at all.

**Service composition:** It is becoming increasingly common to develop new applications by taking existing programs and gluing them together. This is notably the case for many Web-based applications, in particular those known as **Web services**. Web-based middleware can help by standardizing the way Web services are accessed and providing the means to generate their functions in a speciﬁc order. A simple example of how service composition is deployed is formed by mashups:
Web pages that combine and aggregate data from different sources. Well-known mashups are those based on **Google maps** in which maps are enhanced with extra information such as trip planners or real-time weather forecasts.

**Reliability:** The Horus toolkit allows a developer to build an application as a group of processes such that any message sent by one process is guaranteed to be received by all or no other process. As it turns out, such guarantees can greatly simplify developing distributed applications and are typically implemented as part of the middleware.

## 1.2 Design goals ##

Goals of DS:

1. Supporting resource sharing
2. Making distribution transparent
3. Being open
4. Being scalable

### Supporting resource sharing ###

Resources can be virtually anything, peripherals (çevre birimler), storage facilities, data, files, services, and networks. Making distribution transparent is one aim of DS.

### Making distribution transparent ###

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

Users cannot tell where an object is physically located in the system. Achieved by assigning only logical names to resources, that is, names in which the location of a resource is not secretly encoded. Uniform resource locator (URL) http://www.prenhall.com/index.html, which gives no clue about the actual location of Prentice Hall’s main Web server.

**Relocation transparency**

If the entire site may have been moved from one data center to another, users should not notice. This is becoming increasingly important in the context of cloud computing.

**Migration transparency**

Supports the mobility of processes and resources initiated by users, without affecting ongoing communication and operations. Communication between mobile phones, regardless whether two people are actually moving, mobile phones will allow them to continue their conversation. Online tracking and tracing of goods as they are being transported from one place to another, and teleconferencing (partly) using devices that are equipped with mobile Internet.

**Replication transparency**

Resources may be replicated to increase availability or to improve performance by placing a copy close to the place where it is accessed. Hiding the fact that several copies of a resource exist, or that several processes are operating in some form of lockstep mode so that one can take over when another fails. All replicas have the same name. A system that supports replication transparency should generally support location transparency as well.

**Concurrency transparency**

Two independent users may each have stored their files on the same file server or may be accessing the same tables in a shared database and each user does not notice that the other is making use of the same resource.

**Failure transparency**

A user or application does not notice that some piece of the system fails to work properly, and that the system subsequently (and automatically) recovers from that failure.

**Being Open**

A system that offers components that can easily be used by, or integrated into other systems. At the same time, an open distributed system itself will often consist of components that originate from elsewhere.

### Interoperability, composability, and extensibility ###

Deﬁne services through interfaces using an **Interface Deﬁnition Language (IDL)**

**Interoperability** characterizes the extent by which two implementations of systems or components from different manufacturers can co-exist and work together by merely relying on each other’s services as speciﬁed by a common standard

**Portability** characterizes to what extent an application developed for a distributed system A can be executed, without modiﬁcation, on a different distributed system B
that implements the same interfaces as A. 

**Extensible** easy to add new components or replace existing ones without affecting those components that stay in place. An open distributed system should also be extensible. Easy to add parts that run on a different operating system, or even to replace an entire file system

### Separating policy from mechanism ###

System be organized as a collection of relatively small and easily replaceable or adaptable components. Monolithic approach, the older way of development does not provide this.

### Caching in Web browsers ###

Need to consider, Storage, Exemption, Sharing and Refreshing topics. Need to offer a rich set of parameters that the user can set (dynamically).

Trade-off: Strict separation of policies and mechanisms may lead to *highly complex conﬁguration* problems. To solve this, provide reasonable defaults. Self-conﬁgurable systems.

### Being scalable ###

**Size scalability:** Easily add more users and resources to the system without any noticeable loss of performance.
* The computational capacity, limited by the CPUs
* The storage capacity, including the I/O transfer rate
* The network between the user and the centralized service

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

### Scaling techniques ###

In DS, scalibility problems occur because of limited capacity of servers and network. 

1. Scaling up: Increasing memory, upgrading CPUs, or replacing network modules

2. Scaling out: Expanding the distributed system by essentially deploying more machines, there are basically only three techniques can be applied: 

* Hiding communication latencies: applicable in the case of *geographical scalability*. Instead of waiting for a response in the server-side use *asynchronous communication*. In *interactive applications* asynchronous communication cannot be applied. If this is the case, moving part of the computation that is normally done at the server to the client process requesting the service, could be one improvement. 

<figure>
    <a href="/assets/images/PushCodeToClient.png"><img src="/assets/images/PushCodeToClient.png"></a>
</figure>

* Distribution of work Partitioning and distribution: taking a component, splitting it into smaller parts, and subsequently spreading those parts across the system. Internet Domain Name System (DNS). The names in each zone are handled by a single name server. Tree of domains, nonoverlapping zones. *Naming service* is distributed accross machines. Second example is, World Wide Web is partitioned and distributed across a few hundred million servers. Only because of this distribution of documents that the Web has been capable of scaling to its current size.

<figure>
    <a href="/assets/images/DNS.png"><img src="/assets/images/DNS.png"></a>
</figure>

* Replication: Balance the load between components leading to better performance. Geographically widely dispersed systems, having a copy nearby can hide much of the communication latency problems. **Caching** is a special form of replication. Caching is making a copy of a resource, in the proximity of the client accessing that resource. Unlike replication, caching is a decision made by the client of a resource. Caching and replication leads to **consistency**problems. 

Electronic stock exchanges and auctions, requires consistency. Replication requires global synchronization mechanism. 

### Pitfalls ###

Peter Deutsch, at the time working at Sun Microsystems, formulated these ﬂaws as the following false assumptions that everyone makes when developing a distributed application for the first time:

• The network is reliable

• The network is secure

• The network is homogeneous

• The topology does not change

• Latency is zero

• Bandwidth is inﬁnite

• Transport cost is zero

• There is one administrator

## 1.3 Types of distributed systems ##

Distributed computing systems, Distributed information systems, and Pervasive systems

### High performance distributed computing ###

**Cluster computing** the underlying hardware consists of a collection of similar workstations or PCs, closely connected by means of a high-speed local-area network, each node runs the same operating system.

**Grid computing** This subgroup consists of distributed systems that are often constructed as a federation of computer systems, where each system may fall under a different administrative domain, and may be very different when it comes to hardware, software, and deployed network technology. Next step is to outsource entire infrastructure and this ends up in *cloud computing*.

### Note 1.8 (More information: Parallel processing) ###

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

* Hardware: Manage the necessary hardware: processors, routers, but also power and cooling systems. Implemented at data centers and contains the resources that
customers normally never get to see directly. 

* Infrastructure: Provide customers an infrastructure consisting of virtual storage and computing resources. 

* Platform: Platform layer provides to a cloud-computing customer what an operating system provides to application developers, namely the means to easily develop and deploy applications that need to run in a cloud. Amazon S3 storage system is offered to the application developer in the form of an API allowing (locally created)
files to be organized and stored in buckets. 

* Application: Actual applications run in this layer and are offered to users for further customization. (text processors, spreadsheet applications, presentation
applications, and so on). Applications are again executed in the vendor’s cloud. 

* Infrastructure-as-a-Service (IaaS) covering the hardware and infrastructure layer
* Platform-as-a-Service (PaaS) covering the platform layer
* Software-as-a-Service (SaaS) in which their applications are covered

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
READ                    |Read data from a file, a table, or otherwise
WRITE                   |Write data to a file, a table, or otherwise

All-or-nothing property of transactions is also called ACID properties:

* Atomic: To the outside world, the transaction happens indivisibly
* Consistent: The transaction does not violate system invariants
* Isolated: Concurrent transactions do not interfere with each other
* Durable: Once a transaction commits, the changes are permanent

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

File transfer: things that need to be agreed upon:
* File format and layout:
* File management: 
* Update propagation:

Shared database: two major drawbacks.
* There is still a need to design a common data schema
* When there are many reads and updates, a shared database can easily become a performance bottleneck.

Remote procedure call: an RPC allows an application A to make use of the information available only to application B, without giving A direct access to that information

Messaging: eventually the request is delivered, and if needed, that a response is eventually returned as well. 

**Pervasive systems**

Pervasive means "her tarafa yayılan" in Turkish. Introduction of mobile and embedded computing devices, leading to what are generally referred to as pervasive systems. Separation between users and system components is much more blurred. There is often no single dedicated interface, such as a screen/keyboard combination. Instead, a pervasive system is often
equipped with many sensors that pick up various aspects of a user’s behavior. Likewise, it may have a myriad of actuators to provide information and feedback, often even purposefully aiming to steer behavior.

Devices are characterized as being small, battery-powered, mobile, and having only a wireless connection. Internet of Things. 

**Ubiquitous computing systems**

Ubiquitous means "her yerde birden bulunan" in Turkish. User is continuously interacting with the system, often not even being aware that interaction is taking place.

1. (Distribution) Devices are networked, distributed, and accessible in a transparent manner

2. (Interaction) Interaction between users and devices is highly unobtrusive

3. (Context awareness) The system is aware of a user’s context in order to optimize interaction

4. (Autonomy) Devices operate autonomously without human intervention, and are thus highly self-managed
    
    Address allocation: Dynamic Host Conﬁguration Protocol (DHCP) 

    Adding devices: It should be easy to add devices to an existing system. Universal Plug and Play Protocol (UPnP) 

    Automatic updates:

5. (Intelligence) The system as a whole can handle a wide range of dynamic actions and interactions

**Mobile computing systems**

- Mobile implies wireless communication. 

- The location of a device is assumed to change over time.

*Disruption-tolerant networks*: networks in which connectivity between two nodes can simply not be guaranteed. 

<figure>
    <a href="/assets/images/MobileComputing.PNG"><img src="/assets/images/MobileComputing.PNG"></a>
</figure>

With the increasing interest in complex social networks and the explosion of the use of smartphones, combine analysis of social behavior and information dissemination in so-called pocket-switched networks where nodes are formed by people (or actually, their mobile devices), and links are formed when two people encounter each other, allowing their devices to exchange data.

**Sensor networks**

First, sensors do not cooperate but simply send their data to a centralized database located at the operator’s site. The other extreme is to forward queries to relevant sensors and to let each compute an answer, requiring the operator to aggregate the responses. The ﬁrst one requires that sensors send all their measured data through the network, which may waste network resources and energy. The second solution may also be wasteful as it discards the aggregation capabilities of sensors which would allow much less data to be returned to the operator. What is needed are facilities for in-network data processing, similar to the previous example of abstract regions.

<figure>
    <a href="/assets/images/SensorNetworkDatabase.PNG"><img src="/assets/images/SensorNetworkDatabase.PNG"></a>
</figure>


# Chapter 2. Architectures #

The organization of a distributed system can be done one the logical organization of the collection of software components, and second the actual physical realization.

## 2.1 Architectural styles ##

A **component** is a modular unit with well-deﬁned required and provided **interfaces** that is replaceable within its environment. **Connector**, which
is generally described as a mechanism that mediates communication, coordination, or cooperation among components. 

* Layered architectures
* Object-based architectures
* Resource-centered architectures
* Event-based architectures

### Layered architecture: ###

Layered fashion where a component at layer Lj can make a downcall to a component at a lower-level layer Li (with i < j) and generally expects a response. Only in exceptional cases will an upcall be made to a higher-level component.

<figure>
    <a href="/assets/images/LayeredArchitecture.PNG"><img src="/assets/images/LayeredArchitecture.PNG"></a>
</figure>

#### Layered communication protocols ####

Communication-protocol stacks, each layer implements one or several communication services allowing data to be sent from a destination to one or several targets. To this end, each layer offers an **interface** specifying the functions that can be called. In principle, the interface should completely hide the actual implementation of a service. Another important concept in the case of communication is that of a **(communication) protocol**, which describes the rules that parties will follow in order to exchange information. It is important to understand the difference between a service offered by a layer, the interface by which that service is made available, and the protocol that a layer implements to establish communication.

<figure>
    <a href="/assets/images/LayeredCommunicationStack.PNG"><img src="/assets/images/LayeredCommunicationStack.PNG"></a>
</figure>

**Transmission Control Protocol (TCP)**. The protocol speciﬁes which messages are to be exchanged for setting up or tearing down a connection, what needs to be done to preserve the ordering of transferred data, and what both parties need to do to detect and correct data that was lost during transmission.

**Application layering**

* The application-interface level: a part that handles interaction with a user or some external application
* The processing level: a middle part that generally contains the core functionality of the application
* The data level: a part that operates on a database or file system

<figure>
    <a href="/assets/images/SearchEngineLayering.PNG"><img src="/assets/images/SearchEngineLayering.PNG"></a>
</figure>

In data level data is **persistent**, even if no application is running, data will be stored somewhere for next use.

**Object-based and service-oriented architectures**

### Object-based architectures ###  

Each object corresponds to a component, and these components are connected through a procedure call mechanism. A procedure call can also take place over a network, that is, the calling object need not be executed on the same machine as the called object.

<figure>
    <a href="/assets/images/ObjectBasedArchitecture.PNG"><img src="/assets/images/ObjectBasedArchitecture.PNG"></a>
</figure>

Data encapsulating (object’s state) and the operations that can be performed on that data (object's methods). The interface offered by an object conceals implementation details.  

<figure>
    <a href="/assets/images/DistributedObject.PNG"><img src="/assets/images/DistributedObject.PNG"></a>
</figure>

Distributed objects state is not distributed: it resides at a single machine. Only the interfaces implemented by the object are made available on other machines. Such objects are also referred to as remote objects.

In a *service-oriented architecture*, a distributed application or system is essentially constructed as a composition of many different services. Not all of these services may belong to the same administrative organization. Developing a distributed system is partly one of *service composition*, and making sure that those services operate in harmony

### Resource-based architectures ###

Distributed system is huge collection of resources that are individually managed by components. Representational State Transfer (REST). There are four key characteristics of what are known as RESTful

1. Resources are identiﬁed through a single naming scheme

2. All services offer the same interface, consisting of at most four operations,

3. Messages sent to or from a service are fully self-described

4. After executing an operation at a service, that component forgets everything about the caller The last property is also referred to as a stateless execution, 

<figure>
    <a href="/assets/images/RestOps.PNG"><img src="/assets/images/RestOps.PNG"></a>
</figure>

Amazon’s Simple Storage Service (Amazon S3): *objects*, which are essentially the equivalent of files, and *buckets*, the equivalent of directories. **Uniform Resource Identiﬁer (URI)**: http://BucketName.s3.amazonaws.com/ObjectName

### Publish-subscribe architectures ###

Processes can more easily join or leave. Dependencies between processes become as loose as possible.

<figure>
    <a href="/assets/images/FormsOfCoordination.PNG"><img src="/assets/images/FormsOfCoordination.PNG"></a>
</figure>

Referential Coupling - Know name or identifier of the process
Temporarily Coupling - Both processes must be up and running

* Direct Coordination - Cell phone
* Mailbox Coordination - Mails
* Event-Based Coordination - Publish a notification and subscribe
* Shared Data Space - 

<figure>
    <a href="/assets/images/PubSubArchitecture.PNG"><img src="/assets/images/PubSubArchitecture.PNG"></a>
</figure>

Feature of publish-subscribe systems is that communication takes place by describing the events that a subscriber is interested in. (attribute, value) pairs topic-based publish-subscribe systems. (attribute, range) pairs content-based publish-subscribe systems. In this case, the speciﬁed attribute is expected to take on values within a speciﬁed range. 

When subscriptions are matched, there are two possible scenarios. In the ﬁrst case, the middleware may decide to forward the published notiﬁcation, along with
the associated data, to its current set of subscribers, that is, processes with a matching subscription. As an alternative, the middleware can also forward
only a notiﬁcation at which point subscribers can execute a read operation to retrieve the associated data item.

<figure>
    <a href="/assets/images/PubSubDataExchange.PNG"><img src="/assets/images/PubSubDataExchange.PNG"></a>
</figure>

## 2.2 Middleware organization ##

Design patterns that are often applied to the organization of middleware: wrappers and interceptors. Both aim achieving openness.

### Wrappers ###

The interfaces offered by the legacy component are most likely not suitable for all applications. A wrapper or adapter is a special component that offers an interface
acceptable to a client application, of which the functions are transformed into those available at the component. Wrappers have always played an important role in extending systems with existing components.

With N applications we would, in theory, need to develop N × (N − 1) = O(N2) wrappers. Broker, which is logically a centralized component that handles all the accesses between different applications.

<figure>
    <a href="/assets/images/WrapperBroker.PNG"><img src="/assets/images/WrapperBroker.PNG"></a>
</figure>

### Interceptors ###

Interceptor(durdurucu, yol kesen in Turkish) is nothing but a software construct that will break the usual ﬂow of control and allow other (application specific) code to be executed. request-level interceptor - message-level interceptor 

<figure>
    <a href="/assets/images/Interceptor.PNG"><img src="/assets/images/Interceptor.PNG"></a>
</figure>

### Modifiable middleware ###

Designers of middleware to consider the construction of *adaptive software*. Replacing software components at runtime is an example of modifying a system. A system may either be conﬁgured statically at design time, or dynamically at runtime. 

## 2.3 System architecture ##

Centralized and decentralized organizations, as well as various hybrid forms.

### Centralized organizations ###

Clients that request services from servers helps understanding and managing the complexity of distributed systems. 

**Simple client-server architecture**

A server is a process implementing a speciﬁc service, for example, a file system service or a database service. A client is a process that requests a service from a server by sending it a request and subsequently waiting for the server’s reply. This client-server interaction, also known as request-reply behavior.

<figure>
    <a href="/assets/images/ClientServer.PNG"><img src="/assets/images/ClientServer.PNG"></a>
</figure>

When an operation can be repeated multiple times without harm, it is said to be **idempotent.**

Virtually all Internet application protocols are based on reliable TCP/IP connections. In this case, whenever a client requests a service, it first sets up a connection to the server before sending the request. The server generally uses that same connection to send the reply message, after which the connection is torn down. The trouble may be that setting up and tearing down a connection is relatively costly, especially when the request and reply messages are small.

**Multitiered Architectures**

1. A client machine containing only the programs implementing (part of) the user-interface level
2. A server machine containing the rest, that is, the programs implementing the processing and data level

First step, we make a distinction between only two kinds of machines: client machines and server machines, leading to what is also referred to as a **(physically) two-tiered architecture.**

<figure>
    <a href="/assets/images/TwoTieredClientServer.PNG"><img src="/assets/images/TwoTieredClientServer.PNG"></a>
</figure>

From a systems-management perspective, having what are called **fat clients** is not optimal. Instead the **thin clients** as represented by the organizations shown in Figure 2.16(a)–(c) are much easier, perhaps at the cost of less sophisticated user interfaces and client-perceived performance.

Fat clients: ofﬁce suites, many multimedia applications require that processing is done on the client’s side.

Server may sometimes need to act as a client, this leads to **(physically) three-tiered architecture**

<figure>
    <a href="/assets/images/ThreeTieredClientServer.PNG"><img src="/assets/images/ThreeTieredClientServer.PNG"></a>
</figure>

Examples: Transaction processing. Organization of Web sites. Web server acts as an entry point to a site, passing requests to an application server where the actual processing takes place. This application server, in turn, interacts with a database server.

### Decentralized organizations: peer-to-peer systems ### 

A client-server application as a multitiered architecture. We refer to this type of distribution as **vertical distribution**. The characteristic feature of vertical distribution is that it is achieved by placing logically different components on different machines. The term is related to the concept of vertical fragmentation as used in distributed relational databases, where it means that tables are split columnwise, and subsequently distributed across multiple machines

Distribution of the clients and the servers that counts, which we refer to as **horizontal distribution**. In this type of distribution, a client or server may be physically split up into logically equivalent parts, but each part is operating on its own share of the complete data set, thus balancing the load. 

Processes that constitute a peer-to-peer system are all equal interaction between processes is symmetric: each process will act as a client and a server at the same time  acting as a **servant**

**Structured peer-to-peer systems**

Nodes (processes) are organized in an overlay that adheres to a speciﬁc, deterministic topology: a ring, a binary tree, a grid. Each data item that is to be maintained by the system, is uniquely associated with a key, and that this key is subsequently used as an index. To this end, it is common to use a hash function, so that we get: 

key(data item) = hash(data item’s value)

A hypercube is an n-dimensional cube.

<figure>
    <a href="/assets/images/Hypercube.PNG"><img src="/assets/images/Hypercube.PNG"></a>
</figure>

**Unstructured peer-to-peer systems**

Each node maintains an ad hoc list of neighbors. The resulting overlay resembles what is known as a random graph: a graph in which an edge hu, vi between two nodes u and v exists only with a certain probability P[hu, vi]


**Flooding**: In the case of ﬂooding, an issuing node u simply passes a request for a data item to all its neighbors time-to-live or TTL value, giving the maximum number of hops a request is allowed to be forwarded

**Random walks**: At the other end of the search spectrum, an issuing node u can simply try to ﬁnd a data item by asking a randomly chosen neighbor,

**Hierarchically organized peer-to-peer networks**

Many peer-to-peer systems have proposed to make use of special nodes that maintain an index of data items. A collaborative **content delivery network (CDN)**, nodes may offer storage for hosting copies of Web documents allowing Web clients to access pages nearby, and thus to access them quickly. Nodes such as those maintaining an index or acting as a broker are generally referred to as **super peers**. Every regular peer, now referred to as a **weak peer**, is connected as a client to a super peer.

<figure>
    <a href="/assets/images/SuperPeerNetwork.PNG"><img src="/assets/images/SuperPeerNetwork.PNG"></a>
</figure>

In the case of file-sharing networks, it may be better for a weak peer to attach to a super peer that maintains an index of files that the weak peer is currently interested in. In that case, chances are bigger that when a weak peer is looking for a speciﬁc file, its super peer will know where to ﬁnd it.

With super-peer networks a new problem is introduced, namely how to select the nodes that are eligible to become super peer. This problem is closely related to the leader-election problem.

### Hybrid Architectures ###

Some specific classes of distributed systems in which client-server solutions are combined with decentralized architectures.

**Edge-server systems**

These systems are deployed on the Internet where servers are placed “at the edge” of the network. This edge is formed by the boundary between enterprise networks and the actual Internet, for example, as provided by an Internet Service Provider (ISP). Likewise, where end users at home connect to the Internet through their ISP, the ISP can be considered as residing at the edge of the Internet.

<figure>
    <a href="/assets/images/EdgeServerArchitecture.PNG"><img src="/assets/images/EdgeServerArchitecture.PNG"></a>
</figure>

A step further: taking cloud computing as implemented in a data center as the core, additional servers at the edge of the network are used to assist in computations and storage, essentially leading to distributed cloud systems. In the case of **fog computing**, even end-user devices form part of the system and are (partly) controlled by a cloud-service provider.

**Collaborative distributed systems**

**BitTorrent** is a peer-to-peer file downloading system. The basic idea is that when an end user is looking for a file, he downloads chunks of the file from other users until the downloaded chunks can be assembled together yielding the complete file. An important design goal was to ensure *collaboration*. In most file-sharing systems, a significant fraction of participants merely download files but otherwise contribute close to nothing, a phenomenon referred to as **free riding.** To prevent this situation, in BitTorrent a file can be downloaded only when the downloading client is providing content to someone else.

<figure>
    <a href="/assets/images/Bittorrent.PNG"><img src="/assets/images/Bittorrent.PNG"></a>
</figure>

A torrent file contains the information that is needed to download a speciﬁc file. In particular, it contains a link to what is known as a tracker, which is a server that is keeping an accurate account of active nodes that have (chunks of) the requested file.

## 2.4 Example architectures ##

### The Network File System ### 

Many distributed files systems are organized along the lines of client-server architectures, with Sun Microsystem’s Network File System (NFS) being one of the most widely-deployed ones for Unix systems. 

The model underlying NFS and similar systems is that of a remote file service. In this model, clients are offered transparent access to a file system that is managed by a remote server. However, clients are normally unaware of the actual location of files.

Remote access model: the client is offered only an interface containing various ﬁle operations, but the server is responsible for implementing those operations.

Upload/download model a client accesses a ﬁle locally after having downloaded it from the server. Internet’s FTP service

<figure>
    <a href="/assets/images/NFS.PNG"><img src="/assets/images/NFS.PNG"></a>
</figure>

<figure>
    <a href="/assets/images/NFSArchitecture.PNG"><img src="/assets/images/NFSArchitecture.PNG"></a>
</figure>

**Virtual File System (VFS)**, which by now is a de facto standard for interfacing to different (distributed) ﬁle systems. NFS, operations on the VFS interface are either passed to a local ﬁle system, or passed to a separate component known as the NFS client, which takes care of handling access to ﬁles stored at a remote server. In NFS, all client-server communication is done through so-called remote procedure calls (RPCs). The whole idea of the VFS is to hide the differences between various ﬁle systems. The NFS server is responsible for handling incoming client requests.

### The Web ### 

**Simple Web-based systems**

The simplest way to refer to a document is by means of a reference called a Uniform Resource Locator (URL). It speciﬁes where a document is located by embedding the DNS name of its associated server along with a ﬁle name by which the server can look up the document in its local ﬁle system. Furthermore, a URL speciﬁes the  application-level protocol for transferring the document across the network. The communication between a browser and Web server is standardized: they both adhere to the  HyperText Transfer Protocol (HTTP).

<figure>
    <a href="/assets/images/OverallWeb.PNG"><img src="/assets/images/OverallWeb.PNG"></a>
</figure>

HyperText Markup Language, or simply HTML. In that case, the document includes various instructions expressing how its content should be displayed, similar to what one can expect from any decent word processing system.  In particular, they can have complete programs embedded of which Javascript is the one most often deployed.

**Multitiered architectures**

Common Gateway Interface or simply CGI. CGI deﬁnes a standard way by which a Web server can execute a program taking user data as input.

<figure>
    <a href="/assets/images/CGI.PNG"><img src="/assets/images/CGI.PNG"></a>
</figure>

## 2.5 Summary ##
Distributed systems can be organized in many different ways. We can make a distinction between software architecture and system architecture. The latter considers where the components that constitute a distributed system are placed across the various machines. The former is more concerned about the logical organization of the software: how do components interact, in what ways can they be structured, how can they be made independent, and so on. 

A keyword when talking about architectures is architectural style. A style reﬂects the basic principle that is followed in organizing the interaction between the software components comprising a distributed system. Important styles include layering, object-based styles, resource-based styles, and styles in which handling events are prominent. 

There are many different organizations of distributed systems. An important class is where machines are divided into clients and servers. A client sends a request to a server, who will then produce a result that is returned to the client. The client-server architecture reﬂects the traditional way of modularizing software in which a module calls the functions available in another module. By placing different components on different machines, we obtain a natural physical distribution of functions across a collection of machines. 

Client-server architectures are often highly centralized. In decentralized architectures we often see an equal role played by the processes that constitute a distributed system, also known as peer-to-peer systems. In peer-to-peer systems, the processes are organized into an overlay network, which is a logical network in which every process has a local list of other peers that it can communicate with. The overlay network can be structured, in which case deterministic schemes can be deployed for routing messages between processes. In unstructured networks, the list of peers is more or less random, implying that search algorithms need to be deployed for locating data or other processes.

In hybrid architectures, elements from centralized and decentralized or-
ganizations are combined. A centralized component is often used to handle
initial requests, for example to redirect a client to a replica server, which, in
turn, may be part of a peer-to-peer network as is the case in BitTorrent-based
systems.

# Chapter 3 Processes #

Processes: program in execution. From an operating-system perspective, the management and scheduling of processes are perhaps the most important issues to deal with.

## 3.1 Threads ##

Having a ﬁner granularity in the form of multiple threads of control per process makes it much easier to build distributed applications and to get better performance.

### Introduction to threads ###

To execute a program, an operating system creates a number of **virtual processors**, each one for running a different program. To keep track of these virtual processors,the operating system has a **process table**, containing entries to store CPU register values, memory maps, open ﬁles, accounting information, privileges, etc. Jointly, these entries form a **process context**. 

A process context can be viewed as the software analog of the hardware’s processor context. The latter consists of the minimal information that is automatically stored by the hardware to handle an interrupt, and to later return to where the CPU left off. The processor context contains at least the program counter, but sometimes also other register values such as the stack pointer.

A **process** is often deﬁned as a program in execution, that is, a program that is currently being executed on one of the operating system’s virtual processors.

A **thread context** often consists of nothing more than the processor context, along with some other information for thread management.

The performance of a multithreaded application need hardly ever be worse than that of its single-threaded counterpart. In fact, in many cases, multithreading even leads to a performance gain. Second, because threads are not automatically protected against each other the way processes are, development of multithreaded applications requires additional intellectual effort.

Registers of the **memory management unit (MMU)** and invalidate address translation caches such as in the **translation lookaside buffer (TLB).**

**Thread usage in nondistributed systems**

In a single-threaded process, whenever a blocking system call is executed, the process as a whole is blocked.

It becomes possible to exploit parallelism when executing the program on a multiprocessor or multicore system.

Multithreading is also useful in the context of large applications. Collection of cooperating programs, each to be executed by a separate process. This approach is typical for a Unix environment. Cooperation between programs is implemented by means of interprocess communication (IPC) mechanisms. For Unix systems, these mechanisms typically include (named) pipes, message queues, and shared memory segments. The major drawback of all IPC mechanisms is that communication often requires relatively extensive context switching.

<figure>
    <a href="/assets/images/ContextSwitching.PNG"><img src="/assets/images/ContextSwitching.PNG"></a>
</figure>

Software engineering reason to use threads: many applications are simply easier to structure as a collection of cooperating threads.

**Thread implementation**

Thread package to create and destroy threads as well as operations on synchronization variables such as mutexes and condition variables. 

Basically two approaches to implement a thread package. The ﬁrst approach is to construct a thread library that is executed entirely in user space. The second approach is to have the kernel be aware of threads and schedule them.

Many-to-one threading model: multiple threads are mapped to a single schedulable entity.

One-to-one threading model in which every thread is a schedulable entity.

Using processes instead of threads has the important advantage of separating the data space: each process works on its own part of data and is protected from interference from others through the operating system. Thread programming is considered to be notoriously difficult because the developer is fully responsible for managing concurrent access to shared data.

**Threads in distributed systems**

Important property of threads is that they can provide a convenient means of allowing blocking system calls without blocking the entire process in which the thread is running. 

***Multithreaded clients***

The round-trip delay in a wide-area network can easily be in the order of hundreds of milliseconds, or sometimes even seconds.

To hide communication latencies as much as possible, some browsers start displaying data while it is still coming in. 

Web servers have been replicated across multiple machines, where each server provides exactly the same set of Web documents. The replicated servers are located at the same site, and are known under the same name. When a request for a Web page comes in, the request is forwarded to one of the servers, often using a **round-robin strategy** or some other load-balancing technique. 

***When using a multithreaded client***, connections may be set up to different replicas, allowing data to be transferred in parallel, effectively establishing that the entire Web document is fully displayed in a much shorter time than with a nonreplicated server. This approach is possible only if the client can handle truly parallel streams of incoming data. Threads are ideal for this purpose.

* Note that an active thread is not necessarily running; it may be blocked waiting for an I/O request to complete

***Multithreaded servers***

Using multithread is more beneficial in the server side. To understand the benefits of threads for writing server code, consider the organization of a ﬁle server that occasionally has to block waiting for the disk. The ﬁle server normally waits for an incoming request for a ﬁle operation, subsequently carries out the request, and then sends back the reply. One possible, and particularly popular organization is shown in Figure 3.4. Here one thread, the dispatcher, reads incoming requests for a ﬁle operation. The requests are sent by clients to a well-known end point for this server. After examining the request, the server chooses an idle (i.e., blocked) worker thread and hands it the request

<figure>
    <a href="/assets/images/DispatcherWorkerModel.PNG"><img src="/assets/images/DispatcherWorkerModel.PNG"></a>
</figure>

A multithreaded ﬁle server and a single-threaded ﬁle server. A third alternative is to run the server as a big single-threaded ﬁnite-state machine.

<figure>
    <a href="/assets/images/3waystoconstructserver.PNG"><img src="/assets/images/3waystoconstructserver.PNG"></a>
</figure>

Threads make it possible to retain the idea of sequential processes that make blocking system calls and still achieve parallelism. The ﬁnite-state machine approach achieves high performance through parallelism, but uses nonblocking calls, which is generally hard to program and thus to maintain. 

Instead of using threads, we can also use multiple processes to organize a server (leading to the situation that we actually have a multiprocess server). The advantage is that the operating system can offer more protection against accidental access to shared data. However, if processes need to communicate a lot, we may see a noticeable adverse affect on performance in comparison to using threads.

## 3.2 Virtualization ##

Threads and processes build (pieces of) programs that appear to be executed simultaneously. In single processor machine by rapidly switching between threads and processes, the illusion of  parallelism is created. Separation between having a single CPU and being able to pretend there are more can be extended to other resources as well, leading to what is known as **resource virtualization**.

### Principle of virtualization ###










### Power usage effectiveness (PUE) ###
Is a ratio that describes how efficiently a computer data center uses energy; specifically, how much energy is used by the computing equipment (in contrast to cooling and other overhead). PUE was originally developed by a consortium called The Green Grid. [2]

<figure>
    <a href="/assets/images/PUE.svg"><img src="/assets/images/PUE.svg"></a>
    <figcaption>Power Usage Efficiency Formula</figcaption>
</figure>

PUE = Total in DC / Total by server

PUE = (Pservers + Pcrac) / Pserver  => if PUD = 1, it is perfect

6 digit 


**References** 

[1] Andrew S. Tanenbaum and Maarten van Steen. 2006. Distributed Systems: Principles and Paradigms (2nd Edition). Prentice-Hall, Inc., Upper Saddle River, NJ, USA.

[2] https://en.wikipedia.org/wiki/Power_usage_effectiveness