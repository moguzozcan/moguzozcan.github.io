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
Inner classes has direct access to outer classes objects and fields. Inner classes are like the other variables of the outer classes 
and initialized by firstly defining the outer class: 
```java
OuterClass.InnerClass innerObject = outerObject.new InnerClass();
```
An inner class does not exists without an intance of the outer class. "Local Class" and "Anonymous Class" are two types of classes 
of inner class.

Local Class: 
Local classes can be declared inside any type of block like for loop or if else clause or inside a method. There is a confusion on
accessing the members of a local class. I will try to explain it in here. There is a big change in this topic after JDK 8, so let's divide into two:

Before JDK 1.8:
A local class has access to its enclosing, outer, class. Local classes has also access to local variables, but only the final variables. It is necessary for the local class to access a variable. Local classes "captures" that varaible.

After JDK 1.8:
With all the new updates, there is another update in Java 1.8. A term "effectively final" is introduced. If the value of a variable does not change after it's initialization, then that variable is called effectively final. If you want to access a non-final or non-effectivel-final variable, the Java compiler warns you like "local variables referenced from an inner class must be final or effectively final". 

There is another important topic called shadowing. If the name of a variable is the same in outer and inner class, or even in the method, then to avoid confusion we must reach to those variable with some notation. The variable of the inner class shadows the variable of the outer class. Let's look at the following example:
```java
public class ShadowTest {

    public int x = 0;

    class FirstLevel {

        public int x = 1;

        void methodInFirstLevel(int x) {
            System.out.println("x = " + x);
            System.out.println("this.x = " + this.x);
            System.out.println("ShadowTest.this.x = " + ShadowTest.this.x);
        }
    }

    public static void main(String... args) {
        ShadowTest st = new ShadowTest();
        ShadowTest.FirstLevel fl = st.new FirstLevel();
        fl.methodInFirstLevel(23);
    }
}
```
The following is the output of this example:

x = 23
this.x = 1
ShadowTest.this.x = 0
-Refer to member variables that enclose larger scopes by the class name to which they belong!!!

Some important features to remember:
-Local classes are non-static, like inner classes, they cannot refer or contain any static member.
-Local classes defined in static methods can only refer to static members of the enclosing class. ("non-static variable ... cannot be referenced from a static context."
-Interface cannont  inside a block; interfaces are inherently static.
-Static initializers or member interfaces are not allowed in a local class.
-A local class can have static members provided that they are constant variables. (A constant variable is a variable of primitive type or type String that is declared final and initialized with a compile-time constant expression. 

Anonymous Classes:


<a href="http://docs.oracle.com/javase/tutorial/java/javaOO/nested.html">Where</a> did I learned all these stuff. 
