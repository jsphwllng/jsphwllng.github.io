---
layout: default
title: comparing uninitialised variables in java and golang
description: "nill null"
order: 3
---

Recently I had to do some validation of payloads using Golang and I thought it was quite interesting how different languages handle "uninitialised" variables. First we need to discuss what an uninitialised variable is.

```java
  // Zero.java 
  public class Zero {
    public int myNum;
    public float myFloatNum;
    public char myLetter;
    public boolean myBool;
    public String myText;
    public
    String[] myArray;
}
```
When we create a variable in a class (other than Main) in Java we are able to initialise them without providing a value. The normal application of this would be to save memory when performing a search and assigning the result of the search to a string or, for readability, you are awaiting a user to define the variable so you initialise an empty one. We can access these variables in the normal way.

```java
  // Main.java 
  public class Main {
    public static void main(String[] args) {
        Zerotest = new Zero();
        System.out.println(test.myNum);
        System.out.println(test.myFloatNum);
        System.out.println(test.myLetter);
        System.out.println(test.myBool);
        System.out.println(test.myText);
        System.out.println(test.myArray);
    }
} // Output 0 0.0 false null null
```
Interestingly and perhaps annoyingly each of these values are assigned different "empty" values. Most of them seem obvious but the null is more interesting than the rest. Null is a reserved keyword in Java for literal vales. It is case sensitive and is the default value fpr any variables which are not initialised at the time of declaration. The reason it is the default value for the String class is because String is not a primitive type in Java it is defined as java.lang.string. null is not an object or a type but its own special value and you can make any variable null at compile time. Note that we can only do this to reference types int, char, boule. If we attempt to do this with primitive types we get an interesting error java.lang.NullPointerException which hopefully I won't see to much of.
