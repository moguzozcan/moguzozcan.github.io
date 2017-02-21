---
layout: post
title: "Introduction to Data Structures and Algorithms"
date: 2017-02-21
---

Hello guys,
This post will be small. I just encounter a problem where I need to find combination of a number and results would be big that cannot 
be even stored in long, so a BigInteger is required. Here is the code:

```java
private static BigInteger factorial(int N) {
        if(N == 1) {
            return BigInteger.valueOf(1);
        }       
        return BigInteger.valueOf(N).multiply(factorial(N-1));
}
```
