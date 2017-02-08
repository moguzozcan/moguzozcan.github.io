---
layout: post
title: "Analysis of Java Palindrome Checking Algorithms"
date: 2017-02-08
---

Today I've received a task from a company to get a remote job. One of the questions was, "Write an efficient algorithm to check if
a string is palindrome, if the string matches the reverse of a string.". There are three ways of doing this as I can think of, but
the real job is to select most efficient one in terms of time and space complexity. 

The first and most easy one is, using StringBuilder class, reverse the string and check if it is equal to the original string.
Like this:

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

This is actually an easiest way to write a code for palindrome checking. However, this algorithm is not efficient both in terms
of time and space complexity. For that the internal code of the String equals(), and StringBuilder's reverse() and toString()
methods must be analyzed. 

Another way can be to loop through the string. Let's assume we have a string of length n. To find if the string is a palindrome
we need to check if the first character is equal to last, second character is equal to n-1 etc. The first thing that comes to 
mind is a loop that turns n times, assume a for loop, and checks the characters accordingly. A code can be like the following:

```java
private static boolean isPalindrome(String word) {
	  for(int i = 0; i 
}
```
