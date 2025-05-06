
## Chapter 12 : Enumerations, Autoboxing, Static import, Annotations


Key Skills & Concepts
●Understand enumeration fundamentals
●Use the class-based features of enumerations
●Apply the values( ) and valueof( ) methods to enumerations
●Create enumerations that have constructors, instance variables, and methods
●	Employ the ordinal( ) and compareTo( ) methods that enumerations inherit from Enum
●Use Java’s type wrappers
●Know the basics of autoboxing and auto-unboxing
●Use autoboxing with methods
●Understand how autoboxing works with expressions
●Apply static import
●Gain an overview of annotations
●Use the instanceof operator



____

#### Enumerations

In its simplest form, an enumeration is a list of named constants that define a new data type.
An object of an enumeration type can hold only the values that are defined by the list. Thus, an
enumeration gives you a way to precisely define a new type of data that has a fixed number of
valid values.

An enumeration of the months in the year consists of the names January through December. An enumeration of the days of the week is Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, and Saturday.


enumerations are useful whenever you need to define a set of values that represent a collection of items. 

using an enumeration to represent a set of status codes, such as success, waiting, failed, and retrying, which indicate the progress of some action. 

In the past, such values were defined as final variables, but enumerations offer a more structured approach.

____

#### Enumeration Fundamentals

An enumeration is created using the enum keyword.

```java
// An enumeration of transportation.

enum Transport {
	CAR, TRUCK, AIRPLANE, TRAIN, BOAT
}
```


The identifiers CAR, TRUCK, and so on, are called enumeration constants. Each is implicitly declared as a public, static member of Transport.


the enumeration constants’ type is the type of the enumeration in which the constants are declared,

Thus, in the language of Java, these constants are called self-typed, where “self” refers to the enclosing enumeration.


The constants in Transport
use uppercase. (Thus, CAR, not car, is used.) However, the use of uppercase is not required.
In other words, there is no rule that requires enumeration constants to be in uppercase.
Because enumerations often replace final variables, which have traditionally used uppercase,
some programmers believe that uppercasing enumeration constants is also appropriate. There
are, of course, other viewpoints and styles

____


Once you have defined an enumeration, you can create a variable of that type. However, even though enumerations define a class type, you do not instantiate an enum using new. Instead, you declare and use an enumeration variable in much the same way that you do one of the primitive types. For example, this declares tp as a variable of enumeration type Transport:
`Transport tp;`

Because tp is of type Transport, the only values that it can be assigned are those defined by
the enumeration. For example, this assigns tp the value AIRPLANE:
tp = Transport.AIRPLANE;
Notice that the symbol AIRPLANE is qualified by Transport.

___

Two enumeration constants can be compared for equality by using the `= = `relational
operator.

`if(tp == Transport.TRAIN) // ...`

An enumeration value can also be used to control a switch statement. Of course, all of the case statements must use constants from the same enum as that used by the switch expression.

```java
// Use an enum to control a switch statement.
switch(tp) 
{
	case CAR:
		// ...
	case TRUCK:
		// ...
```


in the case statements, the names of the enumeration constants are used without being qualified by their enumeration type name. That is, TRUCK, not Transport.TRUCK, is used. 

This is because the type of the enumeration in the switch expression has already implicitly specified the enum type of the case constants. There is no need to qualify the constants in the case statements with their enum type name. In fact, attempting to do so will cause a compilation error.

___

When an enumeration constant is displayed, such as in a println( ) statement, its name is output. For example, given this statement:

`System.out.println(Transport.BOAT);`

the name BOAT is displayed.

____


```java
// An enumeration of Transport varieties

enum Transport 
{
	CAR, TRUCK, AIRPLANE, TRAIN, BOAT
}

class EnumDemo
{
	public static void main(String[] args)
	{
		Transport tp; // Transport reference
		
		tp = Transport.AIRPLANE;
		// assign tp the constant AIRPLANE
		
		System.out.println("Value of tp: " + tp);
		System.out.println();
		
		tp = Transport.TRAIN;
		//compare two enum values
		if(tp == Transport.TRAIN)
			System.out.println("tp contains TRAIN.\n");
		
		// enum to control switch 
		switch(tp)
		{
			case CAR:
				System.out.println("A car carries people.");
				break;
			case TRUCK:
				System.out.println("A truck carries freight.");
				break;
			case AIRPLANE:
				System.out.println("An airplane flies.");
				break;
			case TRAIN:
				System.out.println("A train runs on rails.");
				break;
			case BOAT:
				System.out.println("A boat sails on water.");
				break;
		}
	}
}
```

```
Value of tp: AIRPLANE

tp contains TRAIN.

A train runs on rails.
```


____

#### Java Enumeration are Class Types

Java implements enumerations as class types. Although you don’t instantiate
an enum using new, it otherwise acts much like other classes. The fact that enum defines a
class enables the Java enumeration to have powers that enumerations in some other languages
do not. For example, you can give it constructors, add instance variables and methods, and
even implement interfaces.


#### The value() and valueOf() methods

All enumerations automatically have two predefined methods: values( ) and valueOf( ).

```java
public static enum-type[ ] values( )

public static enum-type valueOf(String str)
```

The values( ) method returns an array that contains a list of the enumeration constants. 

The valueOf( ) method returns the enumeration constant whose value corresponds to the string
passed in str. In both cases, enum-type is the type of the enumeration.

the return type of `Transport.valueOf("TRAIN")` is Transport. The value returned is TRAIN.

```java
// Use the built-in enumeration methods.

// An enumeration of Transport varieties.
enum Transport 
{
	CAR, TRUCK, AIRPLANE, TRAIN, BOAT
}

class EnumDemo2 
{
	public static void main(String[] args)
	{
		Transport tp;
		
		// use valueOf()
		tp = Transport.valueOf("AIRPLANE");
		
		// use values()
		Transport[] allTransports = Transport.values();
		
		System.out.println("Here are all Transport constants");
		
		for(Transport t : allTransports)
			System.out.println(t);
			
		System.out.println();
		
		System.out.println("tp contains " + tp);
	}
}
```

```
Here are all Transport constants
CAR
TRUCK
AIRPLANE
TRAIN
BOAT

tp contains AIRPLANE
```

#### Constructor Methods, Instance Variables, and Enumerations

each enumeration constant is an object of its enumeration type. Thus, an enumeration can define constructors, add methods, and have instance variables. 

When you define a constructor for an enum, the constructor is called when each enumeration constant is created. 

Each enumeration constant can call any method defined by the enumeration. Each enumeration constant has its own copy of any instance variables defined by the enumeration.

```java
enum Transport
{
	CAR(65), TRUCK(55), AIRPLANE(600), TRAIN(70), BOAT(22);
	// initialization values
	
	private int speed; // instance variable
	
	// constructor
	Transport(int s)
	{
		speed = s;
	}
	
	int getSpeed()
	{ // method
		return speed;
	}
}


class EnumDemo
{
	public static void main(String[] args)
	{
		Transport tp;
		
		System.out.println("Typical speed for an airplane is " +
			Transport.AIRPLANE.getSpeed() +
			" miles per hour.\n");
		
		// Display all transports and speeds
		System.out.println("All Transport speeds: ");
		for(Transport t : Transport.values())
			System.out.println(t + " typical speed is " +
				t.getSpeed() + " miles per hour.");
	}
}
```

```
Typical speed for an airplane is 600 miles per hour.

All Transport speeds:
CAR typical speed is 65 miles per hour.
TRUCK typical speed is 55 miles per hour.
AIRPLANE typical speed is 600 miles per hour.
TRAIN typical speed is 70 miles per hour.
BOAT typical speed is 22 miles per hour.
```

When the variable tp is declared in main( ), the constructor for Transport is called once
for each constant that is specified. Notice how the arguments to the constructor are specified,
by putting them inside parentheses, after each constant, as shown here:

`CAR(65), TRUCK(55), AIRPLANE(600), TRAIN(70), BOAT(22);`

These values are passed to the s parameter of Transport( ), which then assigns this value
to speed.


the last constant, BOAT, is followed by a semicolon. When
an enumeration contains other members, the enumeration list must end in a semicolon.

Because each enumeration constant has its own copy of speed, you can obtain the speed
of a specified type of transport by calling getSpeed( ).
____

Enumerations are appropriate when you are working with lists of items that must be represented by identifiers. A final variable is appropriate when you have a constant value, such as an array size, that will be used in many places. Thus, each has its own use. The advantage of enumerations is that final variables don’t have to be pressed into service for a job for which they are not ideally suited.


There are two restrictions that apply to enumerations. First, an enumeration can’t inherit another class. Second, an enum cannot be a superclass. This means that an enum can’t be extended.

Otherwise, enum acts much like any other class type. The key is to remember that each of the enumeration constants is an object of the class in which it is defined.


#### Enumerations Inherit Enum


you can’t inherit a superclass when declaring an enum, all enumerations automatically
inherit one: java.lang.Enum. This class defines several methods that are available for use by all
enumerations. Most often, you won’t need to use these methods, but there are two that you may
occasionally employ: ordinal( ) and compareTo( ).

The ordinal( ) method obtains a value that indicates an enumeration constant’s position in
the list of constants.

You can compare the ordinal value of two constants of the same enumeration by using the
compareTo( ) method.

___

Traffic Light Program using enum and multithreading
```java
// TrafficLightDemo.java

//enumeration of colors
enum TrafficLightColor {
	RED, GREEN, YELLOW
}

// Computarized traffic light
class TrafficLightSimulator implements Runnable
{
	private TrafficLightColor tlc;
	// to hold light color
	private boolean stop = false; 
	// true to stop simulation
	private boolean changed = false; 
	
	TrafficLightSimulator()
	{ // default constructor putting RED
		tlc = TrafficLightColor.RED;
	}
	
	TrafficLightSimulator(TrafficLightColor init)
	{ // constructor
		tlc = init;
	}
	
	public void run()
	{
		while( !stop )
		{
			try
			{
				switch(tlc)
				{
					case GREEN:
						Thread.sleep(10000);
						break; // green for 10 sec
					case YELLOW:
						Thread.sleep(2000);
						break;  // yellow for 2 sec
					case RED:
						Thread.sleep(12000);
						break; // red for 12 sec
				}
			}
			catch(InterruptedException exc)
			{
				System.out.println(exc);
			}
			changeColor();
		}
	}
	
	// Change Color
	synchronized void changeColor()
	{
		switch(tlc)
		{
			case RED:
				tlc = TrafficLightColor.GREEN;
				break;
			case YELLOW:
				tlc = TrafficLightColor.RED;
				break;
			case GREEN:
				tlc = TrafficLightColor.YELLOW;
		}
		changed = true;
		notify(); // signal light changed
	}
	
	// wait untill a light change occurs
	synchronized void waitForChange()
	{
		try
		{
			while(!changed)
				wait(); // wait for light to change
			changed = false; 
		}
		catch(InterruptedException exc)
		{
			System.out.println(exc);
		}
	}
	
	// Return current color
	synchronized TrafficLightColor getColor()
	{
		return tlc;
	}
	
	// Stop the traffic light
	synchronized void cancel()
	{
		stop = true;
	}
}



class TrafficLightDemo
{
	public static void main(String[] args)
	{
		TrafficLightSimulator tl = new TrafficLightSimulator(TrafficLightColor.GREEN);
		
		Thread thrd = new Thread(tl);
		thrd.start();
		
		for(int i=0; i < 9; i++) 
		{
			System.out.println(tl.getColor());
			tl.waitForChange();
		}
		tl.cancel();
	}
}
```

use of the enumeration simplifies and adds structure to the
code that needs to know the state of the traffic light. Because the light can have only three
states (red, green, or yellow), the use of an enumeration ensures that only these values
are valid, thus preventing accidental misuse.





___

#### Autoboxing

Autoboxing/unboxing greatly simplifies and streamlines code that must convert primitive
types into objects, and vice versa.

Autoboxing/unboxing is directly related to Java’s type wrappers, and to the way that values
are moved into and out of an instance of a wrapper.
we will begin with an overview of the type wrappers and the process of manually boxing and unboxing values.


#### Type Wrappers

Despite the performance benefit offered by the primitive types to hold basic data types, there are times when you will need an object representation. 

For example, you can’t pass a primitive type by reference to a method. Also, many of the standard data structures implemented by Java operate on objects, which means that you can’t use these data structures to store primitive types. To handle these
(and other) situations, Java provides type wrappers, which are classes that encapsulate a primitive type within an object.


The type wrappers are Double, Float, Long, Integer, Short, Byte, Character, and Boolean, which are packaged in java.lang. These classes offer a wide array of methods that allow you to fully integrate the primitive types into Java’s object hierarchy.

All of the numeric type wrappers inherit the abstract class Number. Number declares methods that return the value of an object in each of the different numeric types.
```
byte byteValue( )
double doubleValue( )
float floatValue( )
int intValue( )
long longValue( )
short shortValue( )
```

All of the numeric type wrappers define constructors that allow an object to be constructed
from a given value, or a string representation of that value. 

Here are the constructors defined for Integer and Double:
```
Integer(int num)
Integer(String str) throws NumberFormatException

Double(double num)
Double(String str) throws NumberFormatException
```

However, beginning with JDK 9, the type-wrapper constructors were deprecated, and beginning
with JDK 16, they have been deprecated for removal.



Today, it is strongly recommended that you use one of the valueOf( ) methods to obtain a wrapper object. 

The valueOf( ) method is a static member of all of the wrapper classes and all numeric classes support forms that convert a numeric value or a string into an object. 

For example, here are two forms supported by Integer:
```
static Integer valueOf(int val)

static Integer valueOf(String valStr) throws NumberFormatException
```
Here, val specifies an integer value and valStr specifies a string that represents a properly formatted numeric value in string form. 

Each returns an Integer object that wraps the specified value. 

`Integer iOb = Integer.valueOf(100);`

After this statement executes, the value 100 is represented by an Integer instance. Thus, iOb wraps the value 100 within an object.

___

All of the type wrappers override toString( ). It returns the human-readable form of the
value contained within the wrapper. This allows you to output the value by passing a type
wrapper object to println( ), for example, without having to convert it into its primitive type.

The process of encapsulating a value within an object is called boxing. In the early
days of Java, all boxing took place manually, with the programmer explicitly constructing
an instance of a wrapper with the desired value, as just shown.
`Integer iOb = Integer.valueOf(100);`

The process of extracting a value from a type wrapper is called unboxing. Again, in the
early days of Java, all unboxing also took place manually, using methods to obtain values.

`int i = iOb.intValue();`


The problem is that it is both tedious and error-prone because it requires the programmer
to manually create the appropriate object to wrap a value and to explicitly obtain the proper
primitive type when its value is needed. Fortunately, autoboxing/unboxing fundamentally
improves on these essential procedures.

____

#### Autoboxing Fundamentals

Autoboxing is the process by which a primitive type is automatically encapsulated (boxed)
into its equivalent type wrapper whenever an object of that type is needed. There is no need to
explicitly obtain an object. 

Auto-unboxing is the process by which the value of a boxed object is automatically extracted (unboxed) from a type wrapper when its value is needed. 

There is no need to call a method such as intValue( ) or doubleValue( ).


With autoboxing it is not necessary to manually construct an object in order
to wrap a primitive type. You need only assign that value to a type-wrapper reference. Java
automatically constructs the object for you.

`Integer iOb = 100;  // autobox an int`

To unbox an object, simply assign that object reference to a primitive-type variable. 

`int i = iOb;   // auto-unbox`


```java
// Demonstrate autoboxing/unboxing.

class AutoBox 
{
	public static void main(String[] args) 
	{
		Integer iOb = 100; // autobox an int
		
		int i = iOb; // auto-unbox
		
		System.out.println(i + " " + iOb); // displays 100 100
	}
}
```

#### Autoboxing and Methods

In addition to the simple case of assignments, autoboxing automatically occurs whenever a
primitive type must be converted into an object, and auto-unboxing takes place whenever an
object must be converted into a primitive type. Thus, autoboxing/unboxing might occur when
an argument is passed to a method or when a value is returned by a method.

```java
// Autoboxing/unboxing takes place with
// method parameters and return values.

class AutoBox2 
{
	// This method has an Integer parameter.
	static void m(Integer v) 
	{
		System.out.println("m() received " + v);
	}

	// This method returns an int.
	static int m2() 
	{
		return 10;
	}
	
	// This method return an Integer
	static Integer m3()
	{
		return 99;
	}
	
	public static void main(String[] args)
	{
		m(199); // passing int but needed Integer
		//gets autoboxed
		
		Integer iOb = m2(); 
		// recieves an int, auto unboxed
		System.out.println("Return value from m2() is " + iOb);
		
		int i = m3();
		// reciees Integer
		System.out.println("Return value from m3() is " + i);
		
		iOb = 100;
		System.out.println("Square root of iOb is " + Math.sqrt(iOb));
		// iOb is auto-unboxed and its value promoted to double
		// which is the type needed by sqrt()
	}
}
```

```
m() received 199
Return value from m2() is 10
Return value from m3() is 99
Square root of iOb is 10.0
```

#### Autoboxing/Unboxing Occurs in Expressions


In general, autoboxing and unboxing take place whenever a conversion into an object or from
an object is required. This applies to expressions. Within an expression, a numeric object is
automatically unboxed. The outcome of the expression is reboxed, if necessary.

```java
// Autoboxing/unboxing occurs inside expressions.

class AutoBox3 
{
	public static void main(String[] args) 
	{
		Integer iOb, iOb2;
		int i;
		
		iOb = 99;
		System.out.println("Original value of iOb: " + iOb);
		
		
// The following automatically unboxes iOb,
// performs the increment, and then reboxes
// the result back into iOb.
		++iOb;
		System.out.println("After ++iOb: " + iOb);
		
		
// Here, iOb is unboxed, its value is increased by 10,
// and the result is boxed and stored back in iOb.
		iOb += 10;
		System.out.println("After iOb += 10: " + iOb);
		
		
// Here, iOb is unboxed, the expression is
// evaluated, and the result is reboxed and
// assigned to iOb2.
		iOb2 = iOb + (iOb / 3);
		System.out.println("iOb2 after expression: " + iOb2);
		
		
// The same expression is evaluated, but the
// result is not reboxed.
		i = iOb + (iOb / 3);
		System.out.println("i after expression: " + i);
	}
}
```

```
Original value of iOb: 99
After ++iOb: 100
After iOb += 10: 110
iOb2 after expression: 146
i after expression: 146
```


___

Because of auto-unboxing, you can use integer numeric objects, such as an Integer, to control
a switch statement. For example, consider this fragment:
```java
Integer iOb = 2;

switch(iOb) 
{
	case 1: System.out.println("one");
		break;
	case 2: System.out.println("two");
		break;
	default: System.out.println("error");
}
```
When the switch expression is evaluated, iOb is unboxed and its int value is obtained.
As the examples in the program show, because of autoboxing/unboxing, using nume

____

#### Warning


Because of autoboxing and auto-unboxing, one might be tempted to use objects such as Integer
or Double exclusively, abandoning primitives altogether.

```java
// A bad use of autoboxing/unboxing!
Double a, b, c;
a = 10.2;
b = 11.4;
c = 9.8;
Double avg = (a + b + c) / 3;
```
Although this code is technically correct and does, in fact,
work properly, it is a very bad use of autoboxing/unboxing. It is far less efficient than the
equivalent code written using the primitive type double. The reason is that each autobox and
auto-unbox adds overhead that is not present if the primitive type is used.


In general, you should restrict your use of the type wrappers to only those cases in which
an object representation of a primitive type is required. Autoboxing/unboxing was not added to
Java as a “back door” way of eliminating the primitive types.



____

#### Static Import

Java supports an expanded use of the import keyword. By following import with the
keyword static, an import statement can be used to import the static members of a class
or interface. This is called static import. When using static import, it is possible to refer to
static members directly by their names, without having to qualify them with the name of
their class. This simplifies and shortens the syntax required to use a static member.

```java
// Use static import to bring sqrt() and pow() into view.
import static java.lang.Math.sqrt;

import static java.lang.Math.pow;

class Quadratic 
{
	public static void main(String[] args) 
	{
		// a, b, and c represent the coefficients in the
		// quadratic equation: ax2 + bx + c = 0
		
		double a, b, c, x;
		// Solve 4x2 + x - 3 = 0 for x.
		a = 4;
		b = 1;
		c = -3;
		// Find first solution.
		x = (-b + sqrt(pow(b, 2) - 4 * a * c)) / (2 * a);
		System.out.println("First solution: " + x);
		
		// Find second solution.
		x = (-b - sqrt(pow(b, 2) - 4 * a * c)) / (2 * a);
		System.out.println("Second solution: " + x);
	}
}
```
In this version, the names sqrt and pow are brought into view by these static import statements:
```
import static java.lang.Math.sqrt;
import static java.lang.Math.pow;
```

Without them the equation would have been
`x = (-b + Math.sqrt(Math.pow(b, 2) - 4 * a * c)) / (2 * a);`


___

The second form of static import imports all static members.

`import static pkg.type-name.*;`

`import static java.lang.Math.*;`

If you will be using many static methods or fields defined by a class, then this form lets you bring
them into view without having to specify each individually.



As convenient as static import can be, it is important not to abuse it. Remember, one reason
that Java organizes its libraries into packages is to avoid namespace collisions. When you
import static members, you are bringing those members into the current namespace. Thus, you
are increasing the potential for namespace conflicts and inadvertent name hiding. If you are
using a static member once or twice in the program, it’s best not to import it. Also, some static
names, such as System.out, are so recognizable that you might not want to import them. Static
import is designed for those situations in which you are using a static member repeatedly, such
as when performing a series of mathematical computations. In essence, you should use, but not
abuse, this feature.


you can use static import to import the static members of classes and interfaces you
create. Doing so is especially convenient when you define several static members that are
used frequently throughout a large program. For example, if a class defines a number of
static final constants that define various limits, then using static import to bring them into
view will save you a lot of tedious typing.


#### Annotations (Metadata)


Java provides a feature that enables you to embed supplemental information into a source file.
This information, called an annotation, does not change the actions of a program. However,
this information can be used by various tools, during both development and deployment. For
example, an annotation might be processed by a source-code generator, by the compiler, or
by a deployment tool. The term metadata is also used to refer to this feature, but the term
annotation is the most descriptive, and more commonly used.

An annotation is created through a mechanism based on the interface. Here is a simple
example:
```java
// A simple annotation type.
@interface MyAnno {
	String str();
	int val();
}
```
All annotations consist solely of method declarations. However, you don’t
provide bodies for these methods. Instead, Java implements these methods. Moreover, the
methods act much like fields.

.
.
.
.
.



#### Introducing instanceof


Sometimes it is useful to know the type of an object at run time.

Before we continue, it is necessary to state that instanceof was significantly enhanced by
JDK 17 with a powerful new feature based on pattern matching. Here, the traditional form of
instanceof is introduced.

The traditional form of the instanceof operator has this general form:
`objref instanceof type`

objref is a reference to an object and type is a class or interface type. 
If the object referred to by objref is of the specified type or can be cast to the specified type, then the
instanceof operator evaluates to true.


```java
// Demonstrate the traditional form of the instanceof operator.

class Alpha {
	// ...
}
class Beta extends Alpha {
	// ...
}
class Gamma extends Alpha{
	// ...
}


class InstanceOfDemo 
{
	public static void main(String[] args) 
	{
		Alpha alpha = new Alpha();
		Beta beta = new Beta();
		Gamma gamma = new Gamma();


/*instanceof succeeds when the object is 
the same type as the specified type.*/
		if(alpha instanceof Alpha)
			System.out.println(“alpha is instance of Alpha”);
			
		if(beta instanceof Beta)
			System.out.println(“beta is instance of Beta”);
			
		if(gamma instanceof Gamma)
			System.out.println(“gamma is instance of Gamma”);


/* instanceof succeeds when the object is an
instance of a subclass of the specified type.*/
		if(beta instanceof Alpha)
			System.out.println(“beta is also an instance of Alpha”);
		if(gamma instanceof Alpha)
			System.out.println(“gamma is also an instance of Alpha”);
			
/* This won’t compile because gamma is not 
an instance of Beta or a subclass of Beta. */
		if(gamma instanceof Beta) System.out.println(“Wrong”);



		alpha = beta;
// Because alpha refers to a Beta, this if will succeed
		if(alpha instanceof Beta) {
			System.out.println(“alpha can be cast to Beta”);
			beta = (Beta) alpha;
		}
		
/* This instanceof will fail because alpha refers 
to a Beta object, which cannot be cast to Gamma. 
Thus, it prevents a runtime error */

		if(alpha instanceof Gamma) {
			// This won’t execute.
			gamma = (Gamma) alpha; // error
		}
	}
}
```

```
alpha is instance of Alpha
beta is instance of Beta
gamma is instance of Gamma
beta is also an instance of Alpha
gamma is also an instance of Alpha
alpha refers to a Beta object and can be cast to Beta
```





___


