
## III. Packages and Interfaces

**A. Packages**
1.  How do you define a package in Java? Why are packages needed or what is their purpose?
2.  With the help of a Java program, explain the process of defining a package and then importing and using it in another program.
3.  **Programming Exercise:**
    *   Create a package named `shape`.
    *   Inside this package, create classes representing common shapes like `Square`, `Triangle`, and `Circle`.
    *   Write another program that imports and uses these classes from the `shape` package.
4.  **Programming Exercise:**
    Create a `Balance` class (e.g., for a bank account) and organize it into a package. Demonstrate access protection and importing this package in another class. Write a program to show how classes from different packages can interact using this `Balance` class.

**B. Access Protection, Importing Packages**
1.  List the different access specifiers (access modifiers) available in Java.
2.  Illustrate the use of these access specifiers with respect to class members (variables and methods) with an example.
3.  What are `protected` members? Illustrate with an example how `protected` members can be accessed within the same package and by subclasses in different packages.
4.  Fill in the following table to show the accessibility of class members based on different access modifiers. Illustrate each scenario with a brief example or explanation.

| Context                      | Private | Default (No Modifier) | Protected | Public |
|-----------------------------|---------|------------------------|-----------|--------|
| Same Class                  | ✅      | ✅                     | ✅        | ✅     |
| Same Package Subclass       |         | ✅                     | ✅        | ✅     |
| Same Package Non-subclass   |         | ✅                     | ✅        | ✅     |
| Different Package Subclass  |         |                        | ✅        | ✅     |
| Different Package Non-subclass |      |                        |           | ✅     |

5.  Write a program using packages to demonstrate the visibility of variables and methods when using various types of access specifiers in Java.

**C. Interfaces**
1.  What is an interface in Java? Discuss its significance or use.
2.  Briefly explain how to define an interface and how a class can implement an interface.
3.  How does Java support the implementation of multiple interfaces by a single class? Provide an example.
4.  Differentiate between classes and interfaces, highlighting their key differences, including syntax.
5.  Differentiate between `extends` (for class inheritance) and `implements` (for interface implementation) with respect to inheritance concepts. Illustrate with a suitable example.
6.  What are default interface methods?

**D. Programming with Interfaces**
1.  **Programming Exercise:**
    Write a Java program to implement basic stack operations (e.g., push, pop, peek) using an interface.
2.  **Programming Exercise:**
    Write a Java program to implement basic queue operations (e.g., enqueue, dequeue, peek) using an interface.
3.  **Programming Exercise:**
    Create an interface named `Searchable` with a method `search(int[] arr, int key)` that searches for an element in an array of integers. Create two classes, `LinearSearch` and `BinarySearch`, that implement the `Searchable` interface and provide their own implementations of the `search()` method.
4.  **Programming Exercise:**
    Demonstrate the usage of an interface by:
    *   Creating an interface named `Shape`.
    *   Declaring appropriate abstract methods in `Shape` (e.g., `calculateArea()`). You might also consider data members if appropriate for the interface's design (though interfaces primarily define behavior).
    *   Implementing this `Shape` interface in three classes: `Circle`, `Triangle`, and `Square`, each providing a concrete implementation to compute its area.

---

**IV. Exception Handling**

**A. Exception-Handling Fundamentals**
1.  What is an exception in Java?
2.  Write and explain the general form of an exception-handling block (using `try`, `catch`, `finally`).
3.  Explain the purpose and usage of the `try`, `catch`, and `finally` blocks in exception handling.
4.  List and explain the five keywords commonly associated with exception handling in Java (e.g., `try`, `catch`, `finally`, `throw`, `throws`). Write a program to demonstrate the use of these keywords.

**B. Multiple `catch` Clauses, Nested `try` Statements**
1.  Explain how nested `try` statements work in Java. Provide an example to demonstrate their functionality.
2.  Demonstrate the working of a nested `try` block with an example.

**C. `throw`, `throws`, `finally`**
1.  Differentiate between `throw`, `throws`, and `finally` in the context of Java exceptions. Provide an example illustrating their distinct uses.

**D. Java's Built-in Exceptions**
1.  Explain any four built-in exceptions in Java with suitable examples (e.g., `ArrayIndexOutOfBoundsException`, `NullPointerException`, `ArithmeticException`, `FileNotFoundException`).
2.  Illustrate how exceptions are used in Java to handle runtime exceptions. Design a Java program to demonstrate a common runtime exception, such as `ArrayIndexOutOfBoundsException`.
3.  "Catching an exception is a programmatically good and necessary mechanism." Justify this statement with suitable examples, and design a Java program to demonstrate a built-in runtime exception.

**E. Creating Your Own Exception Subclasses (User-Defined Exceptions)**
1.  Explain how to create your own custom exception classes in Java. Illustrate the process.
2.  Write a program to demonstrate the creation and use of a user-defined exception.
3.  **Programming Exercise:**
    Write a program that takes one integer number as input from the user. The program should throw a custom exception if the input number is greater than 20 (or 10, as per different versions of the question).
4.  **Programming Exercise:**
    Design an exception subclass (e.g., `LowBalanceException`) that throws an exception if a user attempts to withdraw an amount from an account and the remaining balance would fall below a minimum threshold (e.g., Rs. 500).
5.  **Programming Exercise:**
    Design a banking application where users can deposit and withdraw money.
    *   Create a custom exception `InsufficientFundsException` that is thrown when a withdrawal request exceeds the current balance.
    *   Demonstrate how to handle this custom exception using `try-catch` blocks.
    *   Include a `finally` block to display the remaining balance after each transaction attempt (successful or failed).
6.  **Programming Exercise:**
    Create custom exceptions named `InvalidAgeException` and `ArrayOutOfBoundException`. Write a Java program that takes command-line arguments. Based on the arguments (e.g., an age value, an array index), the program should handle the appropriate custom exception gracefully.

