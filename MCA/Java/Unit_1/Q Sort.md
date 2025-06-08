
## I. Introduction to Java

**A. Core Concepts (JVM, Platform Independence)**
1.  What is the Java Virtual Machine (JVM)? Discuss its advantages.
2.  What is the difference between the Java Development Kit (JDK) and the JVM?
3.  Define "platform independence." What makes Java platform-independent? Explain in detail.
4.  Can Java run on any machine? Justify your answer.

**B. Class Fundamentals**
1.  Explain the core concepts of Object-Oriented Programming (OOP) in Java: Encapsulation, Inheritance, and Polymorphism.
2.  Explain each word in the standard Java main method signature: `public static void main (String args[])`.

**C. Declaring Objects, Assigning Object Reference Variables**
1.  What is a class? What is an object? Explain the difference between a class and an object with an example.
2.  How do you define a class and create objects from that class in Java? Provide an illustrative example.
3.  What are access control modifiers (access specifiers) supported by Java? Explain the different types (e.g., public, private, protected, default/package-private) and illustrate their usage and effect on class members with an example.

**D. Introducing Methods, Constructors**
1.  Define a constructor. Discuss its special properties and advantages.
2.  Explain how constructors can be overloaded with the help of an example.
3.  **Programming Exercise:**
    Create a `Swapper` class with:
    *   Two integer instance variables, `x` and `y`.
    *   A constructor that takes two integer parameters to initialize `x` and `y`.
    *   A `getX()` method that returns the value of `x`.
    *   A `getY()` method that returns the value of `y`.
    *   A `void swap()` method that swaps the values of `x` and `y`.
    Then, create a `SwapperDemo` class to test all the methods of the `Swapper` class.
4.  **Programming Exercise:**
    An `Employee` class contains the following members:
    *   Data members: `emp_no`, `emp_name`, `basic`, `da`, `IT`, `Net_sal`.
    *   Member functions: To initialize data, to calculate net salary, and to print data members.
    Write a Java program to read the data for an employee and compute their net salary.
    The `DA` (Dearness Allowance) is 60% of the `basic` pay.
    The `IT` (Income Tax) is 20% of the `basic` pay if the `basic` pay is less than 1,500,000, otherwise, it is 30% of the `basic` pay.
    `Net_sal` = `basic` + `da` - `IT`.

**E. The `this` Keyword, Garbage Collection, The `finalize()` Method**
1.  Discuss the use and purpose of the `this` keyword in Java.
2.  What is Garbage Collection in Java?
3.  What does the `finalize()` method do? Explain its role with an example in the context of garbage collection.

**F. Exploring the `String` Class, Using Command-Line Arguments**
1.  *(Implicit question, often combined with others, e.g., command-line arguments for a specific task)*
2.  Write a Java program to find the area of a rectangle using command-line arguments to pass the length and width. *(This question also relates to the `this` keyword if used in a class context for the rectangle).*

**G. Varargs, `Scanner` Class**
1.  What are variable-length arguments (varargs) in Java? What are the advantages of using them?
2.  Illustrate the use of varargs with a programming example.
3.  Discuss the usage of the `Scanner` class in Java for input operations.


## II. Inheritance

**A. Inheritance Basics**
1.  What is inheritance in Java?
2.  What are the advantages of using inheritance?
3.  Provide an example of inheritance in Java.
4.  Illustrate inheritance with an example, specifically showing the effect of `private` and `default` (package-private) access modifiers on inherited members.

**B. Using `super`, Creating a Multilevel Hierarchy**
1.  Describe the use of the `super` keyword in the context of inheritance. Provide an example.
2.  Illustrate with an example how to invoke a superclass constructor from its subclass using `super()`.
3.  Explain the order of constructor execution in a multilevel hierarchy of classes with an example.

**C. When Constructors Are Called, Method Overriding**
1.  Define method overriding and method overloading. Illustrate both concepts with Java code examples.
2.  What are the rules for method overriding in Java?
3.  How is dynamic polymorphism (runtime polymorphism) achieved through method overriding? Provide an example.

**D. Dynamic Method Dispatch**
1.  What is Dynamic Method Dispatch in Java?
2.  Illustrate Dynamic Method Dispatch (also known as runtime polymorphism) with a programming example.

**E. Using Abstract Classes**
1.  What is an abstract class in Java? Provide an example.
2.  Explain the syntax and use of an `abstract` class.
3.  **Programming Exercise:**
    Create an abstract class named `Shape`.
    Create two subclasses, `Rectangle` and `Triangle`, that extend `Shape`.
    Include appropriate methods in both subclasses to calculate and return their respective areas.

**F. Using `final` with Inheritance**
1.  Explain the syntax and use of the `final` keyword.
2.  Illustrate with an example how the `final` keyword can be used with respect to inheritance (e.g., final classes, final methods).
3.  With the help of suitable examples, explain how the `final` keyword can be used to prevent method overriding.

**G. The `Object` Class**
1.  Explain the role and significance of the `Object` class in Java.
2.  *(Combined Question from original list)* Explain the following with Java code where required:
    *   Varargs
    *   The `Object` class
    *   Use of `final` in inheritance
    *   The `super` keyword

