---
layout: default
title: overloading and overriding methods in java
description: "While studying Java I was introduced to the interesting concept of method overloading."
order: 2
---

[Classes! Constructors! Inheritence!](https://www.youtube.com/watch?v=PUttqdr38t4)

Object-oriented programming is a programming paradigm based on the concept of "objects", which can contain data and code: data in the form of fields, and code, in the form of procedures. A feature of objects is that an object's own procedures can access and often modify the data fields of itself. The simplest way to think about object oriented programming (or OOP) is real world objects.

```java
// Car.java 
  public class Car { 
    public int doors, wheels, speed; 
    public String model, engine, colour; 
    public boolean broken = false; 
  }

```

The most basic class. A car is a class because there can be many types of cars. For example a camper van is a car but it behaves much differently than a sports car. Each share similar properties in that they have wheels, an engine, doors however things may differentiate them such as a roof, a radio or the speed. In this case we can make a car "template" which we will derive the rest of our cars from.

```java
// Main.java 
  public static void main(String[] args) {
    Car c = new Car();
    c.colour = "red";
    c.engine = "big";
    c.wheels = 3;
    c.speed = 10;
    c.doors = 2;
    c.model = "VolkenWagon";
}
```
Here we define a new car called c and assign all of the values to the car. We could just as easily be making a formula 1 car with the class.

```java
  // Car.java
public class Car {
    public int doors, wheels, speed;
    public String
    model, engine, colour;
    public boolean broken = false;
    public void breakdown() {
        broken = !broken;
    }
    public void setModel(String model) {
            this.model = model;
            //this refers to the class not the argument variable } }
```


Classes can have methods like you would normally assign them in the main class. These methods can also interact with the variables that we passed into the object before. as we can see below

```java
// Main.java 
  public class Main {
    public static void main(String[] args) {
            Car
            c = new Car();
            c.colour = "red";
            c.engine = "big";
            c.wheels = 3;
            c.speed = 10;
            c.doors = 2;
            c.model = "VolkenWagon";
            System.out.println(c.broken); //false
            c.breakdown();
            System.out.println(c.broken); //true c.setModel("example");
            //c.model is now "example" } 
      }
```
```java
  // Bank.java 
public class Bank {
    public String customerName, email,
    phoneNumber;
    public int accountNumber, balance;
    public Bank() { // empty
        constructor this("defaultName", "default@email.com", "134", 12345, 0);
    }
    public Bank(String customerName, String email, String phoneNumber, int accountNumber, int balance) { 
        this.email = email;
        this.phoneNumber = phoneNumber;
        this.accountNumber =
            accountNumber;
        this.balance = balance;
    }
}
 // Main.java public class Main {
  public static void main(String[] args) {
    Bank bank = new Bank("joe",
        "joe@emai.com", "22", 20, 20);
    Bank bank2 = new Bank(); // "defaultName",
    "default@email.com", "134", 12345, 0
}
}
```

Constructors are the first function to be called in a class. In this case we overload the Bank constructor so if a empty bank is given it loads itself with default values by using this(). This refers to the instance of a class so, for example, a new instance of Bank's This would only refer to itself and not the parent class.

```java
  // Animal.java
  public class Animal {
  
    private int legs, weight, eyes;
    private String name, colour;
    private boolean furry;
  
    Animal(
      int legs,
      int weight,
      int eyes,
      String name,
      String colour,
      boolean furry
    ) {
      this.legs = legs;
      this.weight = weight;
      this.eyes = eyes;
      this.name = name;
      this.colour = colour;
      this.furry = furry;
    }
  }
  public void eat() {
    System.out.println("nom nom nom "); } } 

    // Dog.java 
    public class Dog extends Animal {
      private boolean
      goodBoy; // unique for a dog and not an animal public Dog(int weight, String
      name, String colour, boolean furry, boolean goodBoy) {
      super(4, weight, 2,
          name, colour, furry); // this means it inherits the Animal constructor but
      were assuming come parameters like legs and eyes this.goodBoy = goodBoy; }
      @Override // Something specific to java? doesnt seem to be required. 
      private void eat() {
          System.out.println("slosh slosh slosh");
      }
      public void
      eatNormally() {
          super.eat()
      }
      private void hiddenFunction() {
          System.out.println("private method");
      }
  }
```


The super here means that you use the constructor from the animal class. But in this case we know dogs always have 4 legs and 2 eyes therefore we don't need to use them as variables in the Dog constructor. We do however need to call the additional variable goodBoy because only dogs can be goodboys. We therefore need to use the normal constructor this.variable = variable. The eat functions get overrides when we define another one in an inherited class. The super in the eatNormally means it referees to parent class and ignores the @Override function defined in the class. The hiddenFunction is not accessible from outside the class hence the private. This means that we cannot call it from outside the class and only methods within the class can call it. For example inside eatNormally we could call hiddenFunction but nowhere else.

this() and super() super can often be confusing. When you use this() to refer to a constructor in the same class. this() needs to be the first statement inside a function or else you will get some errors. You can refer to the constructor of a parent class by using super(). For example the below code creates three different types of rectangles.

```java
  public class Rectangle {
    private int x, y, width, height;
    public Rectangle() {
        this.x = 0;
        this.y = 0;
        this.width = 0;
        this.height = 0;
    }
    public
    Rectangle(int width, int height) {
        this.x = 0;
        this.y = 0;
        this.width = width;
        this.height = height;
    }
    public Rectangle(int x, int y, int width, int height) {
        this.x = x;
        this.y = y;
        this.width = width;
        this.height = height;
    }
}
```

However this is extremely inefficient and by using the this() function we are able to use multiple constructors.

```java
  public class Rectangle {
    private int x, y, width, height;
    public Rectangle() {
            this(0, 0); // calls the second constructor } public Rectangle(int width, int
            height) {
            this(0, 0, width, height); // calls the third constructor } public
            Rectangle(int x, int y, int width, int height) { // initializes all the
                variables this.x = x;
                this.y = y;
                this.width = width;
                this.height = height;
            }
  }
```

This is known as constructor "chaining" as the third constructor will do all the work every time. This leads to fewer lines of [duplicated code](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself).

```java
  // Shape.java 
  public class Shape {
      private int x, y;
      public Shape(int x, int y) {
          this.x = x;
          this.y = y;
      }
  } // Rectangle.java 
  public class Rectangle extends Shape {
      private int width, height;
      public Rectangle(int x, int y) {
          this(x, y, 0, 0);
      }
      public Rectangle(int x, int y, int width, int height) {
          super(x, y);
          this.width = width;
          this.height = height;
      }
  }
```

In rectangle we call the first constructor which then calls the second. The second one calls the parent constructor with parameters x and y. The parent constructor will initialize the x and y variables then the rectangle's constructor will handle the width and height. So ideally you start with the constructor method that has all the variables being assigned and then simplify them or overload them with fewer variables.
