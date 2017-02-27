---
layout: post
title: "Next Permutation Algorithm in Java"
date: 2017-02-27
---

In this post, I will tell you how to write the next permutation algorithm in Java. I've encountered this problem in one of the hackerrank 
<a href=" https://www.hackerrank.com/challenges/bigger-is-greater">challenge.</a>. Java is missing built-in nextPermutation() method,
whereas C++ has <a href="http://www.cplusplus.com/reference/algorithm/next_permutation/">one.</a> So, we need to build our own method.
This method can be used to sort data lexicographically. 

There is a wikipedia <a href="https://en.wikipedia.org/wiki/Permutation#Generation_in_lexicographic_order">link</a> I suggest you to read
to better understand the topic. Now this algorithm is not as complex as it seems. The logic behind this is: 

 -Sort the sequence in increasing order
 -Repeat the following algorithm until it returns false:
    Find the largest index k such that a[k] < a[k + 1]. If no such index exists, the permutation is the last permutation.
    Find the largest index l greater than k such that a[k] < a[l].
    Swap the value of a[k] with that of a[l].
    Reverse the sequence from a[k + 1] up to and including the final element a[n].



```java
private static boolean isPalindrome(String word) {
	StringBuilder sb = new StringBuilder(word);
	String reversed = sb.reverse().toString();
	if(word.equals(reversed)) {
		return true;
	} else {
		return false;
	}    
}
```
