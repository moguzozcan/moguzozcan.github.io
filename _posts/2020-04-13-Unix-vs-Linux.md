---
title: "Unix vs. Linux"
date: 2020-04-13
categories: 
  - UNIX
  - Linux
---

These two terms are always confused and I also was not aware of all the details. In this post, i am sharing the summary of what I learned during my research on this topic.

To understand the difference between these two operating systems we need to know a bit about the history of how we got to where we are today, so let's start with Unix. **UNIX** was invented by two men Ken Thompson and Dennis Ritchie. Dennis Ritchie is famous for inventing the *C programming language* and authored 'C programming language' book with Brian Kernighan, and Ken Thompson invented the *utf-8* character encoding that we all use today and he is the co-inventor of google's *go language*.

In the late 1960s early 1970s Ritchie, Thompson and Kernighan were working on an OS called "multics" which is the abbreviation for "multiplexed information computer services". It was designed to run multiple programs at the same time. Since this was a huge project for the beginning Ritchie and Thompson tried to run the single program version. Than the multics bacame unics and eventually, since remembering computer services 'cs' is hard, it bacame 'UNIX'. 
 
In 1972 Unix was rewritten in just C, then AT&T licensed (since at those times they were forbidden to enter computer market, this is the only thing they could do) the product and sell it to the universities. University of California in Berkeley was one of the universities and they worked on developing the Unix. After some time, AT&T seperated from Bell Labs and they start to sell the commercial Unix version they developed named as Version 5. Then, UCB developed their own version of Unix and they named it as BSD version (Berkeley software distribution). Then some popular OS like HP-UX and Solaris is inherited from version 5. BSD 4.4 light is the version of unix which has no source files that are from AT&T, (which means it can be open sourced) and it led to FreeBSD and Mac OS. 

There is an important topic called **UNIX philosophy**. It is defined as minimalist, modular software development. [3] It contains two idea It is the idea of writing one program which exactly does one thing and does it really well. the idea that a program it's output could become the input to another program which is the idea of pipes.

The BSD and version 5 discussions led to a compatibility discussion and they published the **POSIX** standard. Which actually says that if your program is to compile on this operating system it has to have these api's that have these particular functions.

Richard Stallman and he is responsible for the ideas of free software not free is in no cost but free is in freedom that we have today and also he was responsible for making sure there was the new C compiler the new see runtime library and lots of lots of other tools that were used to able to be able to build a free version of UNIX

**MINIX** which was written by Andrew Tannenbaum and he was using this as an educational tool to teach students the fundamentals of operating system design.

Linus Torvalds wrote **Linux** in 1990 at Finland. He knew about Minix and he wanted to write his own OS. He did it with his own computer and it got really popular. It is now free under GPL license. So, Linux and Unix are not the same, Linux is a Unix like system, or a clone of the Unix. UNIX was actually a product sold by AT&T with version 5 or it was an OS in UCB. Linux does not use their source code, it uses the philosophy of UNIX. Linux distributions: Red Hat, Debian, Fedora etc. Linux is the kernel that's used at the heart of the Android operating system, Chrome OS, Raspberry Pi.

BSD is turned into FreeBSD and now Mac OS is even morphed from BSD. 

The following figure shows how the Unix and Unix-like systems evolved for the last 50 years. I hope you enjoyed. 

<figure>
    <a href="/assets/images/Unix_history-simple.svg"><img src="/assets/images/Unix_history-simple.svg"></a>
    <figcaption>Unix History Tree</figcaption>
</figure>

**References**

[1] https://www.youtube.com/watch?v=jowCUo_UGts

[2] https://tr.wikipedia.org/wiki/Unix

[3] https://en.wikipedia.org/wiki/Unix_philosophy