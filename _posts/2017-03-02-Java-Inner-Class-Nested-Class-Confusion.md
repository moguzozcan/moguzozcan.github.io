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

Why we need nested classes:
-If a class is only used by one class, then it is logical to use it as nested class.
-Using nested class, we can apply one of the OOP concepts, that is encapsulation. 
-It can increase code readability.

Static Nested Class:
We can access static nested classes via outer class name, like that: ``` OuterClass.StaticNestedClass ```. If you would like to 
access the elements of outer class, you need an object reference. This is the same idea in the static class methods, where you also
cannot access the class elements. An example object creation of the static nested class:

```java
OuterClass.StaticNestedClass nestedObject = new OuterClass.StaticNestedClass();
```

Inner Class:


<a href="http://docs.oracle.com/javase/tutorial/java/javaOO/nested.html">Where</a> did I learned all these stuff. 
