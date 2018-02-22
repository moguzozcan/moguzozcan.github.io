---
title: "Analysis of Java Palindrome Checking Algorithms"
date: 2017-02-08
categories: 
  - Jekyll
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
	int len = word.length();	
	for(int i = 0; i < len; i++) {
		if(word.charAt(i) != word.charAt(len - i - 1)) {
			return false;
		}
	}
	return true;
}
```

The above algorithm work correctly, and uses less space than the previous one. Actually, this algorithm has O(1) space 
complexity and O(n) time complexity. But, although this algorithm is better than the first one it still can be improved. 
Looping throught all the length of the string is unnecessary. It will be more than enough to loop only half of the string
length will do the job. Because, if the first half of the string is reversed equal to the second half, then we have a 
palindrome. Here, a question is waken. If the length of the string is odd or even, does that matter? No, actually. 
If we have a string of length 7, abcdcba then in the following algorithm we only loop 3 times, no need to check the middle
character. If the string is abccba, then in the following algorithm, we loop through 3 times and pass all the characters.

```java
private static boolean isPalindrome(String word) {
	int len = word.length();	
	for(int i = 0; i < len / 2; i++) {
		if(word.charAt(i) != word.charAt(len - i - 1)) {
			return false;
		}
	}
	return true;
}
```

So, this algorithm is the most efficient one in terms of time and space complexity. It's space complexity is O(1) since, 
we are allocating any memory location while the algorithm runs. Time complexity is O(n/2), which is better than O(n) in the 
previous one. 

That's all for this post. See you in the next ones :)
