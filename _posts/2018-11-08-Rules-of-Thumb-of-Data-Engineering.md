---
title: "Rules of Thumb of Data Engineering"
date: 2018-11-08
categories: 
  - Amdahl’s Law
  - Moore's Law
  - Gilbert's Law
---

This paper documents some of the main rules we use in engineering database systems.

**2. Storage performance and price**

**Moore’s Law**, which posits that circuit densities increase four fold every three years. Memories get four times larger each three years, or about 100x per decade. " *an extra bit of addressing every 18 months*"

Moore’s Law originally applied only to random access memory (RAM). It has been generalized to apply to microprocessors and to disk storage capacity. Number of transistors in a dense integrated circuit doubles about every two years from wikipedia.

Summarizing the Storage rules of thumb: 
1. Moore’s Law: Things get 4x better every three years. 
2. You need an extra bit of addressing every 18 months. 
3. Storage capacities increase 100x per decade. 
4. Storage device throughput increases 10x per decade. 
5. Disk data cools 10x per decade. 
6. Disk page sizes increase 5x per decade. 
7. NearlineTape:OnlineDisk:RAM storage cost ratios  are approximately 1:3:300. 
8. In ten years RAM will cost what disk costs today. 
9. A person can administer a million dollars of disk storage: that is 30TB of storage today. 
And two observations: 
* Disks are replacing tapes as backup devices. 
* On random workloads, disk mirroring is preferable to 
RAID5 parity because it spends disk space (which is plentiful) to save disk accesses (which are precious)

**3. Amdahl’s system balance rules**

Gene Amdahl is famous for many rules of thumb.

10. Amdahl’s parallelism law: If a computation has a serial component S and a parallel component P, then the maximum speedup is (S+P)/S. 
11. Amdahl’s balanced system law: A system needs a bit of IO per second for each instruction per second: about 8 MIPS per MBps.
12. Amdahl’s memory law: ? ? 1: that is, in a balanced system the MB/MIPS ratio, called alpha (? ), is 1. 
13. Amdahl’s IO law: Programs do one IO per 50,000 instructions. 

**4. Networking: Gilder’s Law**

George Gilder predicted in 1995 that network bandwidth would triple every year for the next 25 years.

14. Gilder’s law: Deployed bandwidth triples every year. 
15. Link bandwidth improves 4x every 3 years.
