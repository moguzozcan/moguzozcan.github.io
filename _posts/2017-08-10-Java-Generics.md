---
layout: post
title: "Java Generics"
date: 2017-08-24
---

Generics occured in https://www.hackerrank.com/challenges/30-generics/problem this challenge, so that I quickly want to remember that.
Generic Types
Generics allow to use and write parametrized types. A generic class is defined like this:

class name<T1, T2, ..., Tn> { /* ... */ }

 A type variable can be any non-primitive type you specify: any class type, any interface type, any array type, or even another type 
 variable.

```java
public interface Pair<K, V> {
    public K getKey();
    public V getValue();
}
```

Generic Methods

Method declarations can also be generic. 

3: public static <T> void sink(T t) { }
4: public static <T> T identity(T t) { return t; }
5: public static T noGood(T t) { return t; } // DOES NOT COMPILE


References 
[1] https://docs.oracle.com/javase/tutorial/java/generics/types.html
[2] https://docs.oracle.com/javase/tutorial/extra/generics/methods.html
