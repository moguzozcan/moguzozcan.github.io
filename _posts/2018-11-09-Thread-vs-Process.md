---
title: "What’s the difference between a thread and a process?"
date: 2018-11-08
categories: 
  - Thread, Process
---

Processes and threads are related to each other but are fundamentally different. 

A **process** can be thought of as an instance of a program in execution. Each process is an independent entity to which system resources (CPU time, memory, etc ) are allocated and each process is executed in a separate address space. One process cannot access the variables and data structures of another process. If you wish to access another process’ resources, inter-process communications have to be used such as pipes, files,sockets etc. A process can have multiple threads.

A **thread** uses the same stack space of a process. A key  difference between processes and threads is that multiple threads share parts of their state. Typically, one allows multiple threads to read and write the same memory (no processes can directly access the memory of another process). However, each thread still has its own registers and its own stack, but other threads can read and write the stack memory. A thread is a particular execution path of a process; when one thread modifies a process resource, the change is immediately visible to sibling threads 