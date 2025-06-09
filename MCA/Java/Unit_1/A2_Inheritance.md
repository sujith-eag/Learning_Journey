
# Inheritance: 

> Inheritance Basics, Using super, Creating a Multilevel Hierarchy, When Constructors Are Called, Method Overriding, Dynamic Method Dispatch, Using Abstract Classes, Using final with Inheritance, The Object Class.


## Inheritance Basics, 

>[!caution] Question
>a. What is inheritance? What are the advantages of inheritance? Give an example of inheritance using java. (8)


**Inheritance** is a fundamental concept in object-oriented programming (OOP) in Java. It is the mechanism by which one class, known as the **subclass**, can acquire the properties (variables) and behaviors (methods) of another class, called the **superclass**. 

The `extends` keyword is used in Java to indicate that a class is inheriting from another. 

This process allows for the creation of hierarchical classifications, where a more specific class inherits traits from a more general class. A subclass is essentially a specialized version of its superclass and represents an "is-a" relationship (e.g., a `Dog` "is an" `Animal`).


**Advantages of Inheritance**: 
* Inheritance provides a natural way to express **hierarchical relationships** between classes. 
- A major advantage is **code reuse**, as the subclass automatically gets the members of its superclass, so they don't need to be redefined.
- This helps to **eliminate redundant code**.
- It **encourages code organization**.
* It promotes the "**is-a**" relationship, where a subclass is a type of its superclass (e.g., a `Dog` "is an" `Animal`).

**Example of Inheritance using Java**: The sources provide an example using `TwoDShape` as a superclass and `Triangle` as a subclass.

- The `TwoDShape` class defines generic attributes common to two-dimensional shapes, such as `width` and `height`.
- The `Triangle` class extends `TwoDShape` using the `extends` keyword.
- By extending `TwoDShape`, the `Triangle` class **inherits all members** defined by `TwoDShape`.
- The `Triangle` class can then add its own unique members, such as a `style` field and methods like `area()` and `showStyle()`.
- Because `Triangle` inherits `width` and `height`, it can directly access these inherited variables within its own methods, like `area()`.
- When an object of the `Triangle` class is created, it can refer to the inherited members (`width` and `height`) directly, as if they were declared within the `Triangle` class itself.

```java
// A superclass
class TwoDShape {
  double width;
  double height;

  void showDim() {
    System.out.println("Width and height are " 
	    + width + " and " + height);
  }
}

// A subclass of TwoDShape
class Triangle extends TwoDShape {
  String style;

  double area() {
    // Triangle can access width and height directly
    return width * height / 2;
  }

  void showStyle() {
    System.out.println("Triangle is " + style);
  }
}

class ShapeDemo {
  public static void main(String args[]) {
    Triangle t1 = new Triangle(); // Creates a Triangle object
    Triangle t2 = new Triangle(); // Creates another Triangle object

    // Set dimensions and style for t1
    t1.width = 4.0; // Accessing inherited member
    t1.height = 4.0; // Accessing inherited member
    t1.style = "isosceles"; // Accessing member unique to Triangle

    // Set dimensions and style for t2
    t2.width = 8.0; // Accessing inherited member
    t2.height = 12.0; // Accessing inherited member
    t2.style = "right"; // Accessing member unique to Triangle

    System.out.println("Info for t1: ");
    t1.showStyle(); // Using method unique to Triangle
    t1.showDim(); // Using inherited method from TwoDShape
    System.out.println("Area is " + t1.area()); // Using method unique to Triangle

    System.out.println(); // Print a blank line

    System.out.println("Info for t2: ");
    t2.showStyle(); // Using method unique to Triangle
    t2.showDim(); // Using inherited method from TwoDShape
    System.out.println("Area is " + t2.area()); // Using method unique to Triangle
  }
}
```

Access control is affected by modifiers like `public`, `private`, and `protected`, as well as package membership. 
Subclass includes all members of its superclass, it cannot access members that are declared `private` in the superclass.

When a subclass object is created, the constructor for the superclass is executed before the constructor for the subclass. If the superclass has a parameterized constructor, the subclass constructor must call a superclass constructor using `super()` as its first statement. If the superclass has no explicit constructor, Java provides a default one that is used.


>[!caution] Question
>
>b. Illustrate inheritance with an example of private and default access. (6)


**Example of Inheritance Illustrating Default and Private Access**: 

Inheritance interacts with Java's access control mechanisms. Access modifiers like `public`, `private`, and `protected`, along with default access (when no modifier is used), determine the visibility of class members.

1. **Default Access**:
    
    - When a class member (variable or method) has **no explicit access modifier**, it is considered to have **default access**.
    - A member with default access is **visible within its package** but not outside its package.
    - In the context of inheritance, if a subclass and its superclass are in the **same package**, the subclass can directly access the default members of its superclass.
2. **Private Access**:
    
    - A member declared as **private** is the most restrictive; it is **accessible only by other members of its own class**.
    - **Inheriting a class does not grant access to its private members**. The private access restriction is not overruled by inheritance.
    - To allow code outside the superclass (including subclasses) to interact with private members, the superclass must provide **public** (or other suitably accessible) **accessor methods**.
The sources provide an example using a `TwoDShape` superclass and a `Triangle` subclass. We can use this to illustrate different access levels.

Let's first look at how the example implicitly demonstrates **default access**:

- In the source example, the `TwoDShape` class has `double width;` and `double height;` declared without any access modifier (like `public` or `private`).
- When a member has no explicit access modifier, it is said to have **default access**.
- A member with default access is **visible within its package but not outside its package**.
- Assuming the `TwoDShape` and `Triangle` classes (and the `ShapeDemo` class with `main`) are all in the same package, then `Triangle` can directly access the `width` and `height` instance variables from `TwoDShape`.

```java
// A superclass
class TwoDShape {
  double width;
  double height; 
  // Default access - accessible within the same package
  private double secretData; 
  // Private access - accessible only within TwoDShape class

  // Parameterised COnstructor
  TwoDShape(double w, double h) {
    width = w;
    height = h;

    this.secretData = w * h * 1.5; // Example calculation
  }

  // Default constructor
  TwoDShape() {
    width = 0.0;
    height = 0.0;
    this.secretData = 0.0;
  }

  // Default access method to show dimensions
  void showDim() 
  {
    System.out.println("Width and height are " 
	    + width + " and " + height);
  }

  // Default accessor method for private data
  double getSecretData() 
  {
    return secretData;
  }
}

// A subclass
class Triangle extends TwoDShape {
  String style; // Default access

  // Parameterized constructor
  Triangle(String s, double w, double h) {
    // Call the superclass constructor FIRST
    super(w, h);
    style = s;
  }

  // Default constructor
  Triangle() {
    super(); // Call the default superclass constructor
    style = "none";
  }

  // Method to calculate area
  double area() {
    // can directly access
    return width * height / 2;
  }

  // Method to show style
  void showStyle() {
    System.out.println("Triangle is " + style);
  }

  // Method to show inherited secret data
  void showInheritedSecretData() {
    System.out.println("Secret Data: " + secretData); 
    // This would cause a compile-time error
    // Cannot directly access private member
    
    // Using accessor method by the superclass
    System.out.println("Inherited Secret Data: " 
	    + getSecretData());
  }
}

// A class to demonstrate usage
class ShapeDemo {
  public static void main(String args[]) {
    // Create Triangle objects using different constructors
    Triangle t1 = new Triangle("isosceles", 4.0, 4.0);
    Triangle t2 = new Triangle("right", 8.0, 12.0);
    Triangle t3 = new Triangle(); // Using default constructors

    System.out.println("Info for t1: ");
    t1.showStyle(); // Accessing method unique to Triangle

    System.out.println("t1.width: " + t1.width); // Direct access to inherited default member
    t1.showDim(); // Accessing inherited method with default access
    System.out.println("Area is " + t1.area()); 
    // Accessing method unique to Triangle (uses inherited default members)
    
    t1.showInheritedSecretData(); 
    // Accessing method unique to Triangle


    System.out.println("\nInfo for t2: ");
    t2.showStyle();
    t2.showDim();
    System.out.println("Area is " + t2.area());
    t2.showInheritedSecretData();

    System.out.println("\nInfo for t3: ");
    t3.showStyle();
    t3.showDim(); // Uses inherited default members (which got default values 0.0 from super() )
    System.out.println("Area is " + t3.area());
    t3.showInheritedSecretData(); // Uses inherited accessor for private data (which got default value 0.0 from super() )
  }
}
```

In this example:

- `TwoDShape` has `width` and `height` with **default access** and `secretData` with **private access**.
- The `Triangle` subclass is in the same package.
- Inside `Triangle`'s `area()` method, it **directly accesses** `width` and `height`, demonstrating that default members are accessible within the same package by a subclass.
- Inside `Triangle`'s `showInheritedSecretData()` method, attempting to directly access `secretData` is shown as an error. Instead, it must call the `getSecretData()` method (which has default access and is in the same package) defined in `TwoDShape` to retrieve the value of the private `secretData`.
- In `main`, objects of type `Triangle` (`t1`, `t2`, `t3`) can directly access inherited members with default access (`width`, `height`) and call inherited methods with default access (`showDim()`, `getSecretData()`) because `ShapeDemo` is also in the same package. This demonstrates the package-level visibility of default members.


```java
// A superclass (assuming default package, so members have default access)
class TwoDShape {
  double width; // Default access
  double height; // Default access

  void showDim() { // Default access
    System.out.println("Width and height are " + width + " and " + height);
  }
}

// A subclass in the same package (default package)
class Triangle extends TwoDShape {
  String style; // Default access unique to Triangle

  double area() {
    // Triangle can directly access width and height because they have default
    // access and Triangle is in the same package as TwoDShape.
    return width * height / 2;
  }

  void showStyle() { // Default access unique to Triangle
    System.out.println("Triangle is " + style);
  }
}

class ShapeDemo { // In the same package
  public static void main(String args[]) {
    Triangle t1 = new Triangle();

    // Can access inherited members (width, height) directly because they
    // have default access and ShapeDemo is in the same package.
    t1.width = 4.0;
    t1.height = 4.0;
    t1.style = "isosceles";

    System.out.println("Info for t1: ");
    t1.showStyle();
    t1.showDim(); // Inherited method is also accessible
    System.out.println("Area is " + t1.area());
  }
}
```

In this scenario, because `TwoDShape` and `Triangle` are in the same package (the default package if no `package` statement is used), the `width` and `height` members (with default access) are fully accessible to `Triangle` and `ShapeDemo`.

Now, let's consider **private access** with inheritance:

- If the `width` and `height` members in the `TwoDShape` superclass were declared as `private`, they would only be accessible by other members **within the `TwoDShape` class itself**.
- **Inheriting a class does not overrule the private access restriction**. A subclass, like `Triangle`, would **not** be able to directly access the `private` members of its superclass, `TwoDShape`.
- To allow subclasses (or any other code outside the superclass) to interact with private members, the superclass must provide **public accessor methods** (like getter and setter methods).

```java
// A superclass with private members
class TwoDShape {
  private double width; // Private access
  private double height; // Private access

  // Public accessor methods to get the values
  double getWidth() { // Default access, assuming same package
    return width;
  }

  double getHeight() { // Default access, assuming same package
    return height;
  }

  // Methods to set the values (can add validation here)
  void setWidth(double w) { // Default access, assuming same package
    width = w;
  }

  void setHeight(double h) { // Default access, assuming same package
    height = h;
  }

  void showDim() { // Default access, assuming same package
    System.out.println("Width and height are " + width + " and " + height);
  }
}

// A subclass
class Triangle extends TwoDShape {
  String style;

  double area() {
    // ERROR: Cannot directly access private members width and height here!
    // return width * height / 2; // This would cause a compile-time error

    // Must use the public accessor methods inherited from TwoDShape
    return getWidth() * getHeight() / 2; // Correct way to access private data
  }

  void showStyle() {
    System.out.println("Triangle is " + style);
  }
}

class ShapeDemo { // In the same package
  public static void main(String args[]) {
    Triangle t1 = new Triangle();

    // ERROR: Cannot directly access private members width and height here!
    // t1.width = 4.0; // This would cause a compile-time error

    // Must use the public methods inherited from TwoDShape
    t1.setWidth(4.0); // Correct way to set private data
    t1.setHeight(4.0); // Correct way to set private data

    t1.style = "isosceles";

    System.out.println("Info for t1: ");
    t1.showStyle();
    t1.showDim(); // Inherited method still works
    System.out.println("Area is " + t1.area());
  }
}
```

This second example illustrates the principle that private members of a superclass are hidden from subclasses, requiring public methods for controlled access, which is consistent with the encapsulation principle of OOP. 



## Using super, Creating a Multilevel Hierarchy, 

a. Describe the use of Super keyword in inheritance. Illustrate with an example. (6)

b. Illustrate with an example, how to invoke super class constructor from the subclass. (6)

c. Explain the order of execution of constructor execution in multilevel hierarchy of classes. (6)


## When Constructors Are Called, Method Overriding, 


c. Illustrate with an example method overloading and method overriding. (8)
a. Explain the following with Java Code: i) Method overriding  ii) Method overloading. (10)

b. List the three rule of method overriding. How to achieve dynamic Polymorphism? Give example. (8)


## Dynamic Method Dispatch, 

b. What is Dynamic method dispatch? Illustrate with an example. (10)

c. What is runtime polymorphism is Java? Explain with example. (8)

## Using Abstract Classes, 

c. What is Abstract Class? Give example. (5)

b. Write syntax and use of the following: i) abstract class ii) final Keyword. (6)

c. Write a program that creates an abstract class ‘Shape’. Create sub classes rectangle and triangle, that include appropriate methods for both sub classes that calculate area of rectangle and triangle. (8)


## Using final with Inheritance, 

b. Illustrate with an example usage of final keyword with respect to inheritance? (6)

b. With the help of suitable examples, explain how "final" can be used to avoid Method overriding. (6)

## The Object Class.

a. Explain the following with Java Code wherever required: i) Varargs  ii) Object Class  iii) Use of final in inheritance   iv) super keyword. (10)

