---
layout: post
title: "Inner Class Nested Class Confusion in Java"
date: 2017-03-02
---

Hello everyone,
For a very long time, I could not really figure out the inner class or nested class stuff. In this post I'll try to understand and 
write about them. So, what is inner class and what differences it has upon a regular Java class?

Java allows us to create classes inside a class. These classes are called "Nested Class". Nested classes are divided into two categories: 
static and non-static. Nested classes that are declared static are called static nested classes. Non-static nested classes are called 
inner classes.

Interestingly, inner classes have access to members of the outer class. Whereas, the static nested classes do not have access to them.
Even if the members of the outer class defined private, these access exists. 

```java
class OuterClass {
    ...
    static class StaticNestedClass {
        ...
    }
    class InnerClass {
        ...
    }
}
```


<a href="http://docs.oracle.com/javase/tutorial/java/javaOO/nested.html">Where</a> did I inspired all these stuff. 
