---
title: "What’s the difference between a thread and a process?"
date: 2018-11-08
categories: 
  - Thread
  - Process
---

Xen, an x86 virtual machine monitor which
allows multiple commodity operating systems to share conventional
hardware in a safe and resource managed fashion, but without sac-
riﬁcing either performance or functionality. This is achieved by
providing an idealized virtual machine abstraction to which oper-
ating systems such as Linux, BSD and Windows XP, can be ported
with minimal effort.

Xen, a high performance resource-managed virtual machine mon-
itor (VMM) which enables applications such as server consolida-
tion [42, 8], co-located hosting facilities [14], distributed web ser-
vices [43], secure computing platforms [12, 16] and application
mobility [26, 37].

Successful partitioning of a machine to support the concurrent
execution of multiple operating systems poses several challenges.
Firstly, virtual machines must be isolated from one another: it is not
acceptable for the execution of one to adversely affect the perfor-
mance of another. This is particularly true when virtual machines
are owned by mutually untrusting users. Secondly, it is necessary
to support a variety of different operating systems to accommodate
the heterogeneity of popular applications. Thirdly, the performance
overhead introduced by virtualization should be small.

full virtu-
alization has the obvious beneﬁt of allowing unmodiﬁed operating
systems to be hosted, it also has a number of drawbacks.

Xen is intended to scale to approximately 100 vir-
tual machines running industry standard applications and services

Xen itself the hypervisor since it operates at a higher privilege level
than the supervisor code of the guest operating systems that it hosts.


Throughout the design and implementation of Xen, a goal has
been to separate policy from mechanism wherever possible. 





Wiki


Xen Project runs in a more privileged CPU state than any other software on the machine.

