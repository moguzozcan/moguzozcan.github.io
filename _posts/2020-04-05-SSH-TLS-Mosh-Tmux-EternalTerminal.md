---
title: "SSH, TLS, Mosh, Tmux, Eternal Terminal"
date: 2020-04-05
categories: 
  - Imperative Programming
  - Declarative Programming
---

I was using iTerm2 and connecting to my devservers through "ssh address_of_server", however i realized that if i try to open more than one connection for the same devserver, my previous connections are dropped. 

It turns out that, ssh itself has some problems, like maintaining the connection by plain ssh is problematic, if your computer goes to sleep or if your connection changes from company proxy to home wifi. And it is also slow for the commands that require high bandwidth. 

**Eternal Terminal**

You can connect to eternal terminal by ```et hostname``` command. 


**Tmux**

Tmux is defined as terminal multiplexer in its official Github website [2]. 

**Mosh**





Starting from macOS Catalina (3 June 2019) WWDC 2019, support only 64 bit applications. Mac uses zsh as the default login shell and interactive shell. 


zsh is highly compatible with the Bourne shell (sh) and mostly compatible with bash, with some differences. For more about zsh and its comprehensive command-line completion system, enter man zsh in Terminal.

**What is Login Shell?**



**What is Interactive Shell?**


**What is Non-Login Shell?**




**Kernel vs. Shell**

**Kernel** is basically the main program in the OS, it talks to your CPU, Memory and IO devices. Kernel has the complete control over anything in your system. Basically, it is the central module in the OS. It is loaded first (before the boot loader) and stays in the RAM, e.g. primary storage. It is generally loaded into the protected area of the RAM, to avoid it being overwritten or attacked. 

Kernel is like a bridge between software and hardware components. 

Example kernels used in OS's:

- Linux kernel is used in Linux, FreeBSD, Android. 
- 


**Monolithic Kernel**

As the name implies, it is one piece of software which includes less lines of code and thus faster. However, the size of the monolithic kernel is generally bigger, because both kernel services and user service resides in the kernel address space. The reason why the monolith kernel is faster although it is bigger in size is that, the communication between the applications and hardware is done by **system calls**.  All the code resides in the same area of the memory. There are some cons of this approach, which are; since the system in coupled, a bug can crash the whole system, and maintaining a single piece of software is harder as in the other type of applications. 

Most famous monolith kernel OS's are Linux, FreeBSD, Android, Microsoft Windows, Solaris. 

**MicroKernel**

MicroKernel is a more decouple kernel system, where user services and kernel services are separated and they are located in different address space. Therefore the size of the microkernel is lesser, since only kernel services take place in the kernel address space. There are  more lines of code in this kernel and its execution is slower than monolith. The communication between applications and hardware are done via message passing (IPC - Inter Process Communication) and thus the microkernels are slower compared to monolith kernels. Since, this is a decoupled system (which means it can easily be extended), if a services crashes system continues to operate. Thus, microkernel is more secure and reliable than monolith kernel. 

Most famous microkernel OS's are Mac OS X and Symbian.

The following image from Wikipedia is a good visualization of the differences between two.

<figure>
    <a href="/assets/images/micro_vs_monolith_kernel.png"><img src="/assets/images/micro_vs_monolith_kernel.png"></a>
    <figcaption>Structure of monolithic and microkernel-based operating systems, respectively</figcaption>
</figure>



**System Call**



**Shell** is basically the terminal that you use to communicate with the Kernel.  




**Boot Loader**

BootLoaders are code pieces that run before any OS or software runs. Their main purpose is to boot the system, in other words bootloader put OS into the memory, RAM from the harddisk. They are very hardware (CPU and board) specific. They are usually stored in ROM, but since ROM size is not sufficient and it is slower, the bootloader code is moved to RAM and executed from there. Then, BootLoader loads the kernel and it can do that from different locations, like memory, file, and network. [5]

The two common boot loaders for Linux are: LILO (LInux LOader) and LOADLIN (LOAD LINux). The GRUB (GRand Unified Bootloader) is popular among RedHat Linux since it is the default bootloader for that. 


<figure>
    <a href="/assets/images/AppleLoginShellOptions.png"><img src="/assets/images/AppleLoginShellOptions.png"></a>
    <figcaption>Apple Login Shell Options</figcaption>
</figure>



**Linux vs Unix**

Unix 

Linux is written by Linus Torvalds in 1991 with C programming language and released under GNU licence. It is nothing but a clone of the UNIX.


**Library functions Vs System calls**

Library functions are nothing but a functions written in some kind of software library, like a strlen() in C. There are two types of library functions: functions which do not call a system call and and the functions which do call a system call. For instance, fopen() is a library function, where is calls the open() system call underneath. 

The main difference of System calls is that, they reach to the system kernel. For example socket() is a system call, it reaches to the kernel to be able to create a network socket. They are the entry points to the OS. [6]

You can debug a library function whereas, it is impossible to debug the system calls. 

The following figure is really great explaning the flow between syscalls and lib functions. 

<figure>
    <a href="/assets/images/system-library-call.png"><img src="/assets/images/system-library-call.png"></a>
    <figcaption>System calls vs Library functions</figcaption>
</figure>




**References**

[1] 

[2] https://github.com/tmux/tmux/wiki

[3] https://techdifferences.com/difference-between-microkernel-and-monolithic-kernel.html

[4] https://en.wikipedia.org/wiki/Microkernel

[5] https://www.cs.tau.ac.il/telux/lin-club_files/linux-boot/slide0002.htm

[6] https://www.thegeekstuff.com/2012/07/system-calls-library-functions/


