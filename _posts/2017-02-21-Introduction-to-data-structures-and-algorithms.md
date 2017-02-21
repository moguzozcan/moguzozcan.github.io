---
layout: post
title: "Introduction to Data Structures and Algorithms"
date: 2017-02-21
---

In this post, I'll talk about the DS and Algorithms topic in general. These topics are the core of the "Computer Science", so they need to
be learn carefully. DS effects memory and algorithm effects the CPU of the machine, so choosing the right DS and algorithm is critical
in overall performance. There is a tradeoff between the memory and CPU time. So, choosing the best is not an easy job.  

Data Structure: A sistematic way of organizing and storing data in an efficient way.

  Correctness:
  Time Complexity:
  Space Complexity: Required memory during the algorithm lifespan.
    Fixed part: Constants, variables etc.
    Variable Part: Recursion stack space, dynamic memory allocation 
 S(P) = C + SP(I)
  
Why need DS:
  Searching faster:
  Handle multiple requests:
  Limited processor:
  
  Worst Case:
  Average Case:
  Best Case:
  
Algorithms:
Search, sort, insert, update, delete

Unambigious, input, output, finite, feasible, independent

Algorithm Analysis:
Priori analysis: CPU memory has no effect.
Posterior analysis:Real, empirical analysis.

Asymptotic analysis:

Big Oh Ο Notation: Measures the worst case, upper bound 
Omega Ω Notation: Measures the best case, lower bound
Theta θ Notation: Measures the average case

Common Asymptotic Notations
Following is a list of some common asymptotic notations −

constant	−	Ο(1)
logarithmic	−	Ο(log n)
linear	−	Ο(n)
n log n	−	Ο(n log n)
quadratic	−	Ο(n2)
cubic	−	Ο(n3)
polynomial	−	nΟ(1)
exponential	−	2Ο(n)

Greedy Algorithms:
They try to find the optimum solution in a given domain. They may or may not lead to a global optimum solutions. Most networking
algorihtms are greedy algorithms.
  
Divide and Conquer Algorithms:
Firstly, divide the problem into smaller ones, sub-problems, until we reach an atomic problem. Generally, a recursive approach
is used to divide problem into atomic, non divisible, problems. Then, solve that smaller problems. Finally, merge all the solved
problems, and reach to final solution.
  
Divide/Break-Conquer/Solve-Merge/Combine

Merge Sort
Quick Sort
Binary Search
Strassen's Matrix Multiplication
Closest pair (points)
  
Dynamic Programming:
Uses memorization, like divide and conquer. Divide to sub-problems. 

-Comparison
Aims to have a global solution unlike greedy.
Uses output to reach a optimum solution unlike divide and conquer.




    
    
