---
title: "Java HashMap vs. HashTable"
date: 2017-07-23
categories: 
  - Jekyll
---
---

When I was solving the third challenge in Cracking the Coding Interview tasks in hackerrank, I've come accross with HashTables. Then I 
realized that I forget the difference between HashMap and HashTable in Java. So, in this post firstly I'll explain their differences
and then I will put my solution to the 3rd challenge. Also, a very short reminder of the hashing topic will be explained. 

Hashing:
Hashing is a very important topic in Computer Science. Converting a key into a computed index operation is called hashing. Hashing 
will provide speed and you can also map infinite number of elements into finite values. So, with some small memory you can store very 
large elements.

One of the main problems of hashing is called collision. Depending on your hash function or the number of elements, two or more elements 
can map to same index. These keys are called synonyms. One way of avoiding this is called chaining. Each colliding pair is stored in a 
linked list data structure. Inserting, deleting and finding elements in a hashtable is O(1), but remember if the hashing is very bad, 
this could get upto O(n).

HashMap vs. HashTable:
Both of mainly does the same job at the end. There is a hidden hash function in behind. When you put somethind inside the container, 
memory location is calculated according to that. When you pull or get something from it, you can reach that element in O(1). Hash function
is used when putting and pulling the element from the container. 

1. HashTable is a sychronized container, whereas HashMap is not. Therefore, HashMap is faster than HashTable but it is not suitable for 
multithread applications. 

2. Putting null objects into HashTable is not possible, but HashMap accepts null key and values. 

Now, the question int the hackerrank is given in the <a href="https://www.hackerrank.com/challenges/ctci-ransom-note"> Hash Tables: Ransom Note</a> link. 

Here is the solution I've come up with using two HashMaps.

```java
public class Solution {

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int m = in.nextInt();
        int n = in.nextInt();
        
        HashMap<String, Integer> map = new HashMap<String, Integer>();
        for(int magazine_i=0; magazine_i < m; magazine_i++){
            String s = in.next();
            if(!map.containsKey(s)) {
                map.put(s, 1);
            } else {
                int integer = map.get(s) + 1;
                map.put(s, integer);
            }                     
        }
        
        for(int ransom_i=0; ransom_i < n; ransom_i++) {
            String s = in.next();
            if(map.containsKey(s)) {
                if(map.get(s) > 0) {
                    int integer = map.get(s) - 1;
                    map.put(s, integer);
                } else {
                    System.out.print("No");
                    return;
                }
            } else {
                System.out.println("No");
                return;
            }
        }
        System.out.println("Yes");
    }
}
``` 



 
