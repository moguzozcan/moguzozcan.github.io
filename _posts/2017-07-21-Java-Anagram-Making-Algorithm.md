---
title: "Java Anagram Making Algorithm"
date: 2017-07-21
categories: 
  - Jekyll
---
---

I've started to work on 30 days of coding challange in hackerrank. The 2nd challange I've solved was is "Given two strings,  
and , that may or may not be of the same length, determine the minimum number of character deletions required to make  and  
anagrams. Any characters can be deleted from either of the strings."

First thing that comes to my mind is delete the common characters from the string and sum length of rest of the strings. This will give 
you how many deletions you need to do. The following algorithm will do the job. numberNeeded() method returns the integer number. 

```java
public static int numberNeeded(String first, String second) {               
    StringBuilder firstStr = new StringBuilder(first);
    StringBuilder secondStr = new StringBuilder(second);

    for(int i = 0; i < firstStr.length(); i++) {            
        for(int j = 0; j < secondStr.length(); j++) {
            if(firstStr.charAt(i) == secondStr.charAt(j)) {
                firstStr.deleteCharAt(i);
                secondStr.deleteCharAt(j);
                i--;
                break;
            }
        }
    }        
    return firstStr.length() + secondStr.length();       
}
```

The time complexity of this algorithm is O(N^2) as you can easily see. Generally, when I first solve a problem, it is not the best or 
optimal solution in terms of the complexity. So, although I passed all the test cases, I look for others solution in the discussion tab.
The key idea is hidden in the problem definition actually. It is guaranteed that  and  consist of lowercase English alphabetic letters 
(i.e.,  through ).

So, why not use some space to decrase time complexity? We can store the occurences of letters in a separate array. For the 1st 
string we count the occurences in the positive way. In the second for loop we subtract the occurences from the countArr. At last,
we ended up with the remaining letters, so if we sum the total we found the required number to have anagrams from two string.

```java
public static int numberNeeded(String first, String second) {
    char[] fArr = first.toCharArray();
    char[] sArr = second.toCharArray();

    int[] countArr = new int[26]; //There are 26 characters in the alphabet

    for (char c : fArr) {  
        countArr[c - 'a']++;
    }

    for (char c : sArr) {  
        countArr[c - 'a']--;
    }

    int total = 0;
    for (int i : countArr) {
        total = total + Math.abs(i);
    }
    return total;        
}
```
