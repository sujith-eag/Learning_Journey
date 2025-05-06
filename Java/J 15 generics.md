
#### Chapter 13 : Generics

Key Skills & Concepts
●Understand the benefits of generics
●Create a generic class
●Apply bounded type parameters
●Use wildcard arguments
●Apply bounded wildcards
●Create a generic method
●Create a generic constructor
●Create a generic interface
●Utilize raw types
●Apply type inference with the diamond operator
●Understand erasure
●Avoid ambiguity errors
●Know generics restrictions


generics added a completely new syntax element and caused changes to many of
the classes and methods in the core API. It is not an overstatement to say that the inclusion of
generics fundamentally reshaped the character of Java.
The topic of generics is quite large, and some of it is sufficiently advanced.

However, a basic understanding of generics is necessary for all Java
programmers. At first glance, the generics syntax may look a bit intimidating, but don’t worry.
Generics are surprisingly simple to use.

____

#### Generics Fundamentals

At its core, the term generics means parameterized types. 

Parameterized types are important because they enable you to create classes, interfaces, and methods in which the type of data upon which they operate is specified as a parameter. 

A class, interface, or method that operates on a type parameter is called generic, as in generic class or generic method.

A principal advantage of generic code is that it will automatically work with the type of data passed to its type parameter.

Many algorithms are logically the same no matter what type of data they are being applied to. For example, a Quicksort is the same whether it is sorting items of type Integer, String, Object, or Thread.
With generics, you can define an algorithm once, independently of any specific type of data, and then apply that algorithm to a wide variety of data types.

____

Object is the superclass of all other classes, an Object reference can refer to any type of object.

Thus, in pre-generics code, generalized classes, interfaces, and methods used Object references to operate on various types of data. The problem was that they could not do so with type safety because casts were needed to explicitly convert from Object to the actual type of data being operated upon. Thus, it was possible to accidentally create type mismatches.

___

Generics add the type safety that was lacking because they make these casts automatic and implicit. In short, generics expand your ability to reuse code and let you do so safely and reliably.

___

Here T is a type parameter, it will be replaced by real type when an object of type Gen is created.
```java
class Gen<T>   // T type parameter
{
	T ob;    // T type object
	
	// Constructor on T type
	Gen(T o)
	{
		ob = o;
	}
	
	// Show type of T
	void showType()
	{
		System.out.println("Type of T is " +
				ob.getClass().getName());
				// object methods
	}
	
	// Return ob of T type
	T getOb()
	{
		return ob;
	}
}


class GenDemo
{
	public static void main(String[] args) 
	{
		Gen<Integer> iOb; // reference to Gen with T as Integer
		iOb = new Gen<Integer>(88);
		// creating and instantiating object
		// of type Gen<Integer>
		
		iOb.showType();
		
		int v = iOb.getOb();
		System.out.println("value: " + v);
		System.out.println();
		
		// Creating Gen object for Strings
		Gen<String> strOb = new Gen<String>("Generics Test");
		strOb.showType();
		String str = strOb.getOb();
		System.out.println("value: " + str);
	}
}
```

```
Type of T is java.lang.Integer
value: 88

Type of T is java.lang.String
value: Generics Test
```

T is the name of a type parameter. This name is used as a placeholder for the actual type that will be passed to Gen when an object is created.

Whenever a type parameter is being declared, it is specified within angle brackets < >. Because
Gen uses a type parameter, Gen is a generic class.


___

there is no special significance to the name T. Any valid
identifier could have been used, but T is traditional. Furthermore, it is recommended that
type parameter names be single-character, capital letters.

is a placeholder for the actual type that will be specified when a Gen object
is created. Thus, ob will be an object of the type passed to T. f type String is
passed to T, then in that instance, ob will be of type String.

___

Object class defines the
method getClass( ). Thus, getClass( ) is a member of all class types. It returns a Class object
that corresponds to the class type of the object on which it is called. Class is a class defined
within java.lang that encapsulates information about a class. Class defines several methods
that can be used to obtain information about a class at run time. Among these is the getName( )
method, which returns a string representation of the class name.

The showType( ) method displays the type of T by calling getName( ) on the Class object returned by the call to getClass( ) on ob.

___

`Gen<Integer> iOb;` creates a version of Gen for integers. Here Integer is the type argument passed to the Gen class parameter.

his effectively creates a version of Gen in which all references to T are translated into references to Integer.

___

Java compiler does not actually create
different versions of Gen, or of any other generic class. the compiler removes all generic type
information, substituting the necessary casts, to make your code behave as if a specific version
of Gen was created. The process of removing generic type information is called erasure.

Calling the Gen constructor, `iOb = new Gen<Integer>(88);`

if type is changed in the instantiation, then will cause compile-time error because it is `Gen<Integer> iOb;`:

`iOb = new Gen<Double>(88.0); // Error!`

This type of checking is one of the main benefits of generics because it ensures type safety.


This makes use of autoboxing to encapsulate 88 which is an int into an Integer.

`iOb = new Gen<Integer>(88);`

`int v = iOb.getOb();`

This also gets autounboxed from Integer to int.

#### Generics Work Only with Reference Types

When declaring an instance of a generic type, the type argument passed to the type parameter must be a reference type. You cannot use a primitive type, such as int or char. 

Therefore, the following declaration is illegal:
```java
Gen<int> intOb = new Gen<int>(53); 
// Error, can't use primitive type
```
Of course, not being able to specify a primitive type is not a serious restriction because you can use the type wrappers to encapsulate a primitive type.

Further, Java’s autoboxing and auto-unboxing mechanism makes the use of the type wrapper
transparent.

____

#### A Generic Class with Two Type Parameters

To specify two or more type parameters, simply use a comma-separated list.

```java
class TwoGen<T, V>
{
	T ob1;    // T type object
	V ob2;    // V type object
	  
	// Constructor
	Gen(T o1, V o2)
	{
		ob1 = o1;
		ob2 = o2;
	}
	
	// Show type of T and V
	void showTypes()
	{
		System.out.println("Type of T is " +
				ob1.getClass().getName());
				
		System.out.println("Type of V is " +
				ob2.getClass().getName());
	}
	
	// Return ob of T type
	T getOb1()
	{
		return ob1;
	}
	
	V getOb2()
	{
		return ob2;
	}
}


class GenDemo
{
	public static void main(String[] args) 
	{
		TwoGen<Integer, String> tgObj = new Gen<Integer, String>(88, "Generics");
		
		tgObj.showTypes();
		
		int v = tgObj.getOb1();
		System.out.println("value: " + v);
		
		int str = tgObj.getOb2();
		System.out.println("value: " + str);
	}
}
```

```
Type of T is java.lang.Integer
Type of V is java.lang.String
value: 88
value: Generics
```

This is also valid
```java
TwoGen<String, String> x = new TwoGen<String, String>("A", "B");
```

#### General for of Generic Class

Syntax for declaring a generic class:
```
class class-name<type-param-list> { // ...
```

Syntax for declaring a reference to a generic class and creating a generic instance:
```
class-name<type-arg-list> var-name =
new class-name<type-arg-list>(cons-arg-list);
```

____

#### Bounded Types

The type parameters could be replaced by any class type. Sometimes it is useful to limit the types that can be passed to a type parameter.

you need some way to tell the compiler that you intend
to pass only numeric types to T. Furthermore, you need some way to ensure that only numeric
types are actually passed.
To handle such situations, Java provides bounded types.


When specifying a type parameter, you can create an upper bound that declares the superclass from which all type arguments must be derived. This is accomplished through the use of an extends clause when specifying the type parameter,

`<T exends superclass>`

This specifies that T can be replaced only by superclass, or subclasses of superclass. Thus, superclass defines an inclusive, upper limit.

```java
class NumericFns<T extends Number> 
{
	T num;
	
	NumericFns(T n) 
	{
		num = n;
	}
	
	// Return the reciprocal.
	double reciprocal() 
	{
		return 1 / num.doubleValue();
	}
	
	// Return the fractional component.
	double fraction() 
	{
		return num.doubleValue() - num.intValue();
	}
}
```
This compiles because now the `doubleValue()` method available to Number class and compiler knows only Numeric types will be the Type parameters like Integer, Double which are subclass of Number. So String cannot be passed.


___

Bounded types are especially useful when you need to ensure that one type parameter is
compatible with another.

Here V must be either same type as T or subclass of T.
```java
class Pair<T, V extends T>
{
	T first;
	V second;
	
	Pair(T a, V b)
	{
		first = a;
		second = b;
	}
	// ....
}
```


```java
// this is valid, same type
Pair<Integer, Integer> x = new Pair<Integer, Integer>(1, 2);

// Integer subclass of Number so valid
Pair<Number, Integer> y = new Pair<Number, Integer>(10.4, 12);

// Error
Pair<Number, String> z = new Pair<Number, String>(10.4, "12");
```

___

#### Using Wildcard Arguments


As useful as type safety is, sometimes it can get in the way of perfectly acceptable constructs.

assume that you want to add a method called absEqual( ) that returns true if two NumericFns objects contain numbers whose absolute values are the same.
What type do you specify for NumericFns’ type parameter? 

```java
// This won't work!

boolean absEqual(NumericFns<T> ob) 
{
	if(Math.abs(num.doubleValue()) ==
		Math.abs(ob.num.doubleValue()) return true;
		
	return false;
}
```


The wildcard argument is specified by the ?, and it represents an unknown type.

```java
// Determine if the absolute values of two
// objects are the same.

boolean absEqual(NumericFns<?> ob) 
{
	if(Math.abs(num.doubleValue()) ==
		Math.abs(ob.num.doubleValue())) return true;
		
	return false;
}
```

Here, `NumericFns<?>` matches any type of NumericFns object, allowing any two NumericFns objects to have their absolute values compared.


___

```java
class NumericFns<T extends Number> 
{
	T num;
	
	// Pass reference to numeric object.
	NumericFns(T n) 
	{
		num = n;
	}
	
	// Return the reciprocal.
	double reciprocal() 
	{
		return 1 / num.doubleValue();
	}

	// Return the fractional component.
	double fraction() 
	{
		return num.doubleValue() - num.intValue();
	}

// Determine if the absolute values of two
// objects are the same.
	boolean absEqual(NumericFns<?> ob) 
	{
		if(Math.abs(num.doubleValue()) == 
			Math.abs(ob.num.doubleValue())) return true;
			
		return false;
	}
// ...
}


// Demonstrate a wildcard.
class WildcardDemo 
{
	public static void main(String[] args) 
	{
		NumericFns<Integer> iOb =
			new NumericFns<Integer>(6);

		NumericFns<Double> dOb =
			new NumericFns<Double>(-6.0);

		NumericFns<Long> lOb =
			new NumericFns<Long>(5L);
			
		System.out.println("Testing iOb and dOb.");
		if(iOb.absEqual(dOb))
			System.out.println("Absolute values are equal.");
		else
			System.out.println("Absolute values differ.");
			
System.out.println();

		System.out.println("Testing iOb and lOb.");
		if(iOb.absEqual(lOb))
			System.out.println("Absolute values are equal.");
		else
			System.out.println("Absolute values differ.");
	}
}
```

```
Testing iOb and dOb.
Absolute values are equal.

Testing iOb and lOb.
Absolute values differ.
```




`if(iOb.absEqual(dOb))`

In the first call, iOb is an object of type `NumericFns<Integer>` and dOb is an object of type `NumericFns<Double>`. However, through the use of a wildcard, it is possible for iOb to pass
dOb in the call to absEqual( ).


wildcard does not affect what type of NumericFns objects can be created. This is governed by the extends clause in the NumericFns declaration. The wildcard simply matches any valid NumericFns object.

___


#### Bound Wildcards

Wildcard arguments can be bounded in much the same way that a type parameter can be
bounded. A bounded wildcard is especially important when you are creating a method that is
designed to operate only on objects that are subclasses of a specific superclass.

to establish an upper bound for a wildcard, use the following type of wildcard
expression:
```
<? extends superclass>
```

```java
// Here, the ? will match A or any class type
// that extends A.

static void test(Gen<? extends A> o) {
	// ...
}
```


You can also specify a lower bound for a wildcard by adding a super clause to a wildcard
declaration. 
```
<? super subclass>
```


____

#### Generic Methods

methods inside a generic class can make use of a class type parameter and are, therefore, automatically generic relative to the type parameter. 

However, it is possible to declare a generic method that uses one or more type parameters of its own.

Furthermore, it is possible to create a generic method that is enclosed within a nongeneric class.


Here class is not generic but the method is generic so how the parameter type is applied differs. 
```java
class GenericMethodDemo 
{
	// Determine if the contents of two arrays are the same.

	static <T extends Comparable<T>, V extends T> 
		boolean arraysEqual(T[] x, V[] y) 
		{ // A generic method.
		
		// If array lengths differ, then the arrays differ.
			if(x.length != y.length) 
				return false;
			
			for(int i=0; i < x.length; i++)
				if(!x[i].equals(y[i]))
					return false; 
					// arrays differ
					
			return true; 
	// contents of arrays are equivalent
	}


	public static void main(String[] args) 
	{
		Integer[] nums = { 1, 2, 3, 4, 5 };
		Integer[] nums2 = { 1, 2, 3, 4, 5 };
		Integer[] nums3 = { 1, 2, 7, 4, 5 };
		Integer[] nums4 = { 1, 2, 7, 4, 5, 6 };
		
	// The type arguments for T and V are
	// implicitly determined when the method is called.
		if(arraysEqual(nums, nums))
			System.out.println("nums equals nums");
			
		if(arraysEqual(nums, nums2))
			System.out.println("nums equals nums2");
	
		if(arraysEqual(nums, nums3))
			System.out.println("nums equals nums3");
			
		if(arraysEqual(nums, nums4))
			System.out.println("nums equals nums4");
			
	// Create an array of Doubles
		Double[] dvals = { 1.1, 2.2, 3.3, 4.4, 5.5 };
	
	
	// This won't compile because nums and dvals
	// are not of the same type.
		if(arraysEqual(nums, dvals))
			System.out.println("nums equals dvals");
	}
}
```

```
nums equals nums
nums equals nums2
```


___

```java
static <T extends Comparable<T>, V extends T> 
	boolean arraysEqual(T[] x, V[] y) 
	{
```

The type parameters are declared before the return type of the method. 


`T extends Comparable<T>`. 

Comparable is an 'interface' declared in java.lang. A class that implements Comparable defines objects that can be ordered. Thus, requiring an upper bound of Comparable ensures that `arraysEqual( )` can be used only with objects that are capable of being compared. 

Comparable is 'generic interface', and its type parameter specifies the type of objects that it compares.

`V extends T`,  Type V is upper-bounded by T. Thus, V must be either the same as type T or a subclass of T.

`arraysEqual( )` is static, enabling it to be called
independently of any object. generic methods can be either static or nonstatic. There is no restriction in this regard.


syntax for a generic method:
```
<type-param-list> ret-type meth-name(param-list) { // ...
```
In all cases, type-param-list is a comma-separated list of type parameters. Notice that for a generic method, the type parameter list precedes the return type.

____

#### Generic Constructors

A constructor can be generic, even if its class is not.
```java
class Summation
{
	private int sum;
	
	<T extends Number> Summation(T arg)
	{
		sum = 0;
		
		for(int i=0; i<= arg.intValue(); i++)
			sum += i;
	}
	int getSum()
	{
		return sum;
	}
}

class GenConsDemo
{
	public static void main(String[] args) 
	{
		Summation ob = new Summation(4.0);
		
		System.out.println("Summation of 4.0 is " + ob.getSum() );
	}
}
```

Summation( ) specifies a type parameter that is bounded by Number, a Summation object can be constructed using any numeric type, including Integer, Float, or Double.

No matter what numeric type is used, its value is converted to Integer by calling intValue( ), and the summation is computed.

___

#### Generic Interfaces

the standard interface `Comparable<T>` was used to ensure that elements of two arrays could be compared.

```java
interface Containment<T>
{
	boolean contains(T o);
}

// class that implements genric must also
// be a genric class

class MyClass<T> implements Containment<T>
{
	T[] arrayRef;
	
	MyClass(T[] o)
	{
		arrayRef = o;
	}
	
	// Implement contains()
	public boolean contains(T o)
	{
		for(T x : arrayRef)
			if(x.equals(o) ) 
				return true;
			return false;
	}
}

class GenIFDemo
{
	public static void main(String[] args) 
	{
		Integer[] x = {1,2,3};
		
		MyClass<Integer> ob = new MyClass<Integer>(x);
		
		if(ob.contains(2))
			System.out.println("2 is in ob");
		else
			System.out.println("2 is NOT in ob");
		
		if(ob.contains(5))
			System.out.println("5 is in ob");
		else
			System.out.println("5 is NOT in ob");
			
		if(ob.contains(9.25)) // Illegal
			System.out.println("9.25 is in ob");
	}
}
```

```
2 is in ob
5 is NOT in ob
```


if a class implements a generic interface, then that class must also be generic, at least to the extent that it takes a type parameter that is passed to the interface.

```java
class MyClass implements Containment<T> {
// Wrong!
```
This declaration is wrong because MyClass does not declare a type parameter, which means that there is no way to pass one to Containment. In this case, the identifier T is simply unknown and the compiler reports an error.

___

The type parameter(s) specified by a generic interface can be bounded.

```
interface Containment<T extends Number> {
```

Now, any implementing class must pass to Containment a type argument also having the
same bound.
```
class MyClass<T extends Number> implements Containment<T> {
```

Containment now requires a type that extends Number, the
implementing class (MyClass in this case) must specify the same bound. Furthermore, once this
bound has been established, there is no need to specify it again in the implements clause.

```
// This is wrong!

class MyClass<T extends Number>
	implements Containment<T extends Number> 
{ // Wrong!
```
this declaration is incorrect and won’t compile:

____

#### Raw Types and Legacy Code

Because support for generics did not exist prior to JDK 5, it was necessary for Java to provide
some transition path from old, pre-generics code. Simply put, pre-generics legacy code had to
remain both functional and compatible with generics. This meant that pre-generics code must
be able to work with generics, and generic code must be able to work with pre-generics code.
To handle the transition to generics, Java allows a generic class to be used without any type
arguments. This creates a raw type for the class. This raw type is compatible with legacy code,
which has no knowledge of generics.

The main drawback to using the raw type is that the type safety of generics is lost.

```java
class Gen<T> 
{
	T ob; //
	....
}

class RawDemo {
	public static void main(String[] args) 
	{
		// Create a Gen object for Integers.
		Gen<Integer> iOb = new Gen<Integer>(88);
		
		Gen raw = new Gen(98.6);
		// when no type argument is supplied
		// a raw type os created
```
no type arguments are specified. In essence, this creates a Gen object whose type T is replaced by Object.


___

#### Type Inference with the Diamond Operator

to create an instance of TwoGen, you must use a
statement similar to the following:

```java
TwoGen<Integer, String> tgOb =
	new TwoGen<Integer, String>(42, "testing");
```
Here, the type arguments (which are Integer and String) are specified twice, it is a bit more verbose than it needs to be.

To address this situation, JDK 7 added a
syntactic element that lets you avoid the second specification.
Today, the preceding declaration can be rewritten as shown here:
```java
TwoGen<Integer, String> tgOb = 
		new TwoGen<>(42, "testing");


class-name<type-arg-list> var-name = 
		new class-name< >(cons-arg-list);
```

instance creation portion simply uses < >, which is an empty type argument list. This is referred to as the diamond operator. It tells the compiler to infer the type arguments needed by the constructor in the new expression.

___

mostly for use in declaration statements, type inference can also be applied to parameter passing.

```java
boolean isSame(TwoGen<T, V> o) 
{
	if(ob1 == o.ob1 && ob2 == o.ob2) return true;
	else return false;
}
```

then the following call is legal:

```java
if(tgOb.isSame(new TwoGen<>(42, "testing"))) 
	System.out.println("Same");
```

In this case, the type arguments for the arguments passed to isSame( ) can be inferred from the parameters’ types. They don’t need to be specified again.



#### Local Variable Type Inference and Generics

```java
TwoGen<Integer, String> tgObj = 
	new TwoGen<Integer, String>(42, "testing");
	
//using local variable type inference:
var tgOb = new TwoGen<Integer, String>(42, "testing");
```

the type of tgOb is inferred to be TwoGen<Integer, String> because that is the type of its initializer.

#### Erasure

Any changes to the syntax of the Java language, or to the JVM, had to avoid breaking older code. 

The way Java implements generics while satisfying this constraint is through the use of erasure.

In general, here is how erasure works. When your Java code is compiled, all generic type information is removed (erased). This means replacing type parameters with their bound type, which is Object if no explicit bound is specified, and then applying the appropriate casts (as determined by the type arguments) to maintain type compatibility with the types specified by the type arguments. 

The compiler also enforces this type compatibility. This approach to generics means that no type parameters exist at run time. They are simply a
source-code mechanism.

#### Ambiguity Errors

Ambiguity errors occur when erasure causes two seemingly distinct generic declarations to
resolve to the same erased type, causing a conflict.

```java
// Ambiguity caused by erasure on
// overloaded methods.

class MyGenClass<T, V> 
{
	T ob1;
	V ob2;
	// ...
	
	// These two overloaded methods are ambiguous
	// and will not compile.
	void set(T o) 
	{
		ob1 = o;
	}
	void set(V o) 
	{
		ob2 = o;
	}
}
```

Inside MyGenClass, an attempt is made to overload set( ) based on parameters of type T and V.

First, as MyGenClass is written there is no requirement that T and V actually be different
types. For example, it is perfectly correct (in principle) to construct a MyGenClass object as
shown here:

```java
MyGenClass<String, String> obj = 
	new MyGenClass<String, String>()
```

In this case, both T and V will be replaced by String. This makes both versions of set( ) identical, which is, of course, an error.

Thus, the overloading of set( ) as attempted in MyGenClass is inherently ambiguous.

___

#### Some Generic Restrictions

Type Parameters Can’t Be Instantiated
```java
// Can't create an instance of T.
class Gen<T> {
	T ob;
	Gen() {
		ob = new T(); // Illegal!!!
	}
}
```

the compiler has no way to know what type of object to create. T is simply a placeholder.


Restrictions on Static Members

No static member can use a type parameter declared by the enclosing class.

```java
class Wrong<T> {
	// Wrong, no static variables of type T.
	static T ob;

	// Wrong, no static method can use T.
	static T getOb() {
		return ob;
	}
}
```

Generic Array Restrictions

First, you cannot instantiate an array whose element type is a type parameter. 

Second, you cannot create an array of type-specific generic references.

```java
class Gen<T extends Number> {
	T ob;
	T[] vals;
	Gen(T o, T[] nums)
	{
		ob = o;
		
		// this is illegal
		vals = new T[10]; 
	}
}

```

`// Gen<Integer>[] gens = new Gen<Integer>[10]; // Wrong!`

