
## Chapter 14 : Lambda Expressions and Method References

Key Skills & Concepts
●Know the general form of a lambda expression
●Understand the definition of a functional interface
●Use expression lambdas
●Use block lambdas
●Use generic functional interfaces
●Understand variable capture in a lambda expression
●Throw an exception from a lambda expression
●Understand the method reference
●Understand the constructor reference
●Know about the predefined functional interfaces in java.util.function

___


#### Introducing Lambda Expressions

Key to understanding the lambda expression are two constructs. 
The first is the lambda expression,
itself. 

The second is the functional interface.

A lambda expression is, essentially, an anonymous (that is, unnamed) method. However,
this method is not executed on its own. Instead, it is used to implement a method defined by a
functional interface. Thus, a lambda expression results in a form of anonymous class. Lambda
expressions are also commonly referred to as closures.


A functional interface is an interface that contains one and only one abstract method. Thus, a functional interface typically represents a single action.
For example, the standard interface Runnable is
a functional interface because it defines only one method: run( ). Therefore, run( ) defines the action of Runnable. 

Furthermore, a functional interface defines the target type of a lambda expression. 

Here is a key point: a lambda expression can be used only in a context in which a target type is specified. 

A functional interface is sometimes referred to as a
SAM type, where SAM stands for Single Abstract Method.


#### Lambda Expression Fundamentals

operator, sometimes referred to as the lambda operator or the arrow operator, is –>. It divides a lambda expression into two parts. The left side specifies any parameters required by the lambda expression. 
On the right side is the lambda body, which
specifies the actions of the lambda expression.

Lambda body can be single expression or consist of block of code.

___

```java
() -> 98.6;
```
This lambda expression takes no parameters, thus the parameter list is empty. It returns the
constant value 98.6. The return type is inferred to be double. Therefore, it is similar to the
following method:

```java
double myMeth() { return 98.6; }
```
the method defined by a lambda expression does not have a name

___

```java
() -> Math.random() * 100;
```

This lambda expression obtains a pseudo-random value from Math.random( ), multiplies it by
100, and returns the result. It, too, does not require a parameter.

____

When parameter is needed
```java
(n) -> 1.0 / n;
```

This lambda expression returns the reciprocal of the value of parameter n.

Although it is possible to explicitly specify the type of a parameter, often you won’t need to because, in many cases, its type can be inferred.

This returns true or false of type boolean
```java
(n) -> (n % 2)==0;

n -> (n % 2)==0;
```

When a lambda expression has only one parameter,
it is not necessary to surround the parameter name with parentheses when it is specified on
the left side of the lambda operator.



___


#### Functional Interfaces

functional interface is an interface that specifies only one abstract method.

an interface method is abstract only if it is does not specify an implementation

a functional interface can include default, static, or private methods, but in all cases it must have one and only one abstract method. 

Default methods are not abstract. Neither are static or private interface methods. 
Because non-default, non-static, non-private interface methods are implicitly abstract, there is no need to use the abstract modifier (although you can specify it, if you like).

```java
interface MyValue {
	double getValue();
}
```

MyValue is a functional interface, and its function is defined by getValue( ).
because the method getValue( ) is implicitly abstract, and it is the only method defined by
MyValue.

___

a lambda expression can be specified only in a context in which a target type is defined. 

One of these contexts is created when a lambda expression is assigned to a 'functional interface reference'. 

```java
interface MyValue {
	double getValue();
}

// Create a reference to a MyValue instance.
MyValue myVal;

// Use a lambda in an assignment context.
myVal = () -> 98.6;

// lambda expression is assigned to that interface reference

// simplified
MyValue myVal = () -> 98.6;
```

This lambda expression is compatible with getValue( ) because, it has no parameters and returns a double result.

In general, the type of the abstract method defined
by the functional interface and the type of the lambda expression must be compatible. If they
aren’t, a compile-time error will result.


Here, myVal is initialized with the lambda expression.

When a lambda expression occurs in a target type context, an instance of a class is automatically created that implements the functional interface, with the lambda expression defining the behavior of the abstract method declared by the functional interface. 

When that method is called through the target, the lambda expression is executed. Thus, a lambda
expression gives us a way to transform a code segment into an object.

```java
System.out.println("A constant value: " 
			+ myVal.getValue());
```
will return "A constant value: 98.6"

___

obtained when getValue( ) is called.
If the lambda expression takes one or more parameters, then the abstract method in the
functional interface must also take the same number of parameters.

```java
interface MyParamValue
{
	double getValue(double v);
}

MyParamValue myPval = (n) -> 1.0 / n;

System.out.println("Reciprocal of 4 is " 
		+ myPval.getValue(4.0));
```
getValue( ) is implemented by the lambda expression referred to by myPval,
which returns the reciprocal of the argument. In this case, 4.0 is passed to getValue( ), which
returns 0.25.

the type of n is not specified. Rather, its type is inferred from the context. In this case, its type is inferred from the parameter type of getValue( ) as defined by the MyParamValue interface, which is
double. It is also possible to explicitly specify the type of a parameter in a lambda expression.

`(double n) -> 1.0 / n;`

In general, the type and number of the lambda expression’s parameters must be compatible with the method’s parameters and its return type.


___


Other target type contexts include variable initialization, return statements, and method arguments, to name a few.

___


```java
// A functional interface.

interface MyValue
{
	double getValue();
}

interface MyParamValue
{
	double getValue(double v);
}

class LambdaDemo
{
	public static void main(String[] args)
	{
		MyValue myVal = () -> 98.6;
		
		System.out.println("A constant value: " + myVal.getValue());
		
		MyParamValue myPval = (n) -> 1.0/n;
		System.out.println("Reciprocal of 4 is " + myPval.getValue(4.0));
		System.out.println("Reciprocal of 8 is " + myPval.getValue(8.0));
	}
}
```

```
A constant value: 98.6
Reciprocal of 4 is 0.25
Reciprocal of 8 is 0.125
```

___

Not matching the types and parameters
```java
// calling with incompatible return type
myVal = ()-> "three";
// Error! String not compatible with double!

// no parameter
myPval = () -> Math.random(); 
// Error! Parameter required!
```

___

#### What it means is 

The gist is make a class without a body(interface) and atleast one abstract method (functional interface) in it which has the return type and parameters defined but no functionality.

The lambda expression which has no name but just a parameter and action (which acts as body and variable assignment) is assigned to an instance of the interface.... so essentially making it into an instance of a class (object) so now it can be used as any class and method by passing the parameters of suitable type and the output of the expression should match the output type.

It is making an object out of an interface without defining and writing one more concrete object. a by pass to get the class object and adding a body to it.


___

```java

/* A functional interface that takes two int parameters 
and returns a boolean result. */

interface NumericTest {
	boolean test(int n, int m);
}

class LambdaDemo2
{
	public static void main(String[] args)
	{
	
		NumericTest isFactor = (n, d) -> (n % d) == 0;
		// lambda expression to find is d is factor of n
	
		if( isFactor.test(10, 2) )
			System.out.println("2 is a factor of 10");
			
		if(!isFactor.test(10, 3))
			System.out.println("3 is not a factor of 10");
		System.out.println();
	
	
	/* Using same functional interface to find small
	and large by changing the expression for
	another instance*/
	
		NumericTest lessThan = (n, m) -> (n < m);
		//calling test()
		if(lessThan.test(2, 10))
			System.out.println("2 is less than 10");
			
		if(!lessThan.test(10, 2))
			System.out.println("10 is not less than 2");
		System.out.println();
	
	
	/* lambda expression to return true if the
	absolute value are equal */
	
		NumericTest absEqual = (n, m) -> (n < 0 ? -n : n) == (m < 0 ? -m : m);
		
		if(absEqual.test(4, -4))
			System.out.println("Absolute values of 4 and -4 are equal.");
			
		if(!lessThan.test(4, -5))
			System.out.println("Absolute values of 4 and -5 are not equal.");
		System.out.println();
	}
}
```

```
2 is a factor of 10
3 is not a factor of 10

2 is less than 10
10 is not less than 2

Absolute values of 4 and -4 are equal.
Absolute values of 4 and -5 are not equal.
```

using different reference variables called isFactor, lessThan, and absEqual,
as the original program does, makes it very clear to which lambda expression each variable
refers.

there is no need to use three separate NumericTest reference variables because the same one could have been used for all three tests by re assigning the lambda expression.
```java
NumericTest myTest;

myTest = (n, d) -> (n % d) == 0;

myTest = (n, m) -> (n < m);

myTest = (n, m) -> (n < 0 ? -n : n) == (m < 0 ? -m : m);
```


Similar input using string can also be made
```java
interface StringTest {
	boolean test(String aStr, String bStr);
}

class LambdaDemo3 
{
	public static void main(String[] args)
	{
/* This lambda expression determines if one string is part of another. */
		StringTest isIn = (a, b) -> a.indexOf(b) != -1;

		String str = "This is a test";
		System.out.println("Testing string: " + str);
		
		if(isIn.test(str, "is a"))
			System.out.println("'is a' found.");
		else
			System.out.println("'is a' not found.");
			
			
		if(isIn.test(str, "xyz"))
			System.out.println("'xyz' Found");
		else
			System.out.println("'xyz' not found");
	}
}
```

```
Testing string: This is a test
'is a' found.
'xyz' not found
```

the lambda expression uses the indexOf( ) method defined by the String class
to determine if one string is part of another.

____


#### Block Lambda Expressions

Lambda expression where lambda bodies consisting of a single expression are referred to as expression bodies, and expression lambdas.

Second type consists of more than one expression in a block of code called block body. called block lambdas.

in a block lambda you can declare variables, use loops, specify if and switch
statements, create nested blocks, and so on. One key difference, however, is that you must explicitly use a return
statement to return a value. This is necessary because a block lambda body does not represent
a single expression.

```java
// A block lambda that finds the smallest positive factor

interface NumericFunc
{
	int func(int n);
}

class BlockLambdaDemo
{
	public static void main(String[] args)
	{
		NumericFunc smallestF = (n) -> {
			int result = 1;
			
			// get absolute calue
			n = n<0 ? -n : n;
			
			for(int i=2; i<=n/i; i++)
			{
				if( (n%i) == 0 )
				{
					result = i;
					break;
				}
			}
			return result;
		};  // ; for expression block
		System.out.println("Smallest factor of 12 is " + smallestF.func(12));
		System.out.println("Smallest factor of 11 is " + smallestF.func(11));
	}
}
```

```
Smallest factor of 12 is 2
Smallest factor of 11 is 1
```

____

When a return statement occurs within a lambda expression, it simply causes a return from the lambda. It does not cause an enclosing method to return.

____

#### Generic Functional Interfaces

A lambda expression, itself, cannot specify type parameters. Thus, a lambda expression cannot be generic. (Of course, because of type inference, all lambda expressions exhibit some “generic-like” qualities.) However, the functional interface associated with a lambda expression can be generic.


In this case, the target type of the lambda expression is determined, in part, by the type argument or arguments specified when a functional interface reference is declared.

```java
// genric functional interface
interface SomeTest<T> 
{
	boolean test(T n, T m);
}

class GenericFunctionalInterfaceDemo 
{
	public static void main(String[] args)
	{
		// if one integer is factor of another
		SomeTest<Integer> isFactor = 
			(n, d) -> (n % d) == 0;
		
		if(isFactor.test(10,2))
			System.out.println("2 is a factor of 10");
		System.out.println();
		
		
		
	// determines if one string is part of another.	
		SomeTest<String> isIn = 
			(a, b) -> a.indexOf(b) != -1;
		
		String str = "Generic Functional Interface";
		
		System.out.println("Testing string: " + str);
		
		if(isIn.test(str, "face"))
			System.out.println("'face' is found.");
		else
			System.out.println("'face' not found.");
	}
}
```

```
2 is a factor of 10

Testing string: Generic Functional Interface
'face' is found.
```

T specifies the type of both parameters for test( ). This means that it is compatible with any lambda expression that takes two parameters of the same type and returns a boolean result.

____
#### Pass a Lambda Expression as a Argument

A lambda expression can be used in any context that provides
a target type. The target contexts used by the preceding
examples are assignment and initialization. Another one is when a lambda expression is passed
as an argument. In fact, passing a lambda expression as an argument is a common use of
lambdas. Moreover, it is a very powerful use because it gives you a way to pass executable code
as an argument to a method. This greatly enhances the expressive power of Java.

```java
interface StringFunc 
{
	String func(String str);
}

class LambdaArgumentDemo 
{
	static String changeStr(StringFunc sf, String s) 
	{
		return sf.func(s);
	}
	
	public static void main(String[] args)
	{
		String inStr = "Lambda Expressions Expand Java";
		String outStr;
		
		System.out.println("Here is input string: " + inStr);
		
		StringFunc reverse = (str) ->
		{
			String result = "";

			for(int i = str.length()-1; i >= 0; i--)
				result += str.charAt(i);
				
			return result;
		};
		outStr = changeStr(reverse, inStr);

		System.out.println("The string reversed: " + outStr);


		outStr = changeStr((str) ->
		{ 
			str.replace(' ', '-'), inStr);
		System.out.println("The string with spaces replaced: " + outStr);


		outStr = changeStr((str) -> {
			String result = "";
			char ch;
			
			for(int i = 0; i < str.length(); i++ ) 
			{
				ch = str.charAt(i);
				if(Character.isUpperCase(ch))
					result += Character.toLowerCase(ch);
				else
					result += Character.toUpperCase(ch);
			}
			return result;
			}, inStr);
			
		System.out.println("The string in reversed case: " + outStr);
	}
}
```



#### Lambda Expressions and Variable Capture


Variables defined by the enclosing scope of a lambda expression are accessible within the
lambda expression. For example, a lambda expression can use an instance variable or static
variable defined by its enclosing class. A lambda expression also has access to this (both
explicitly and implicitly), which refers to the invoking instance of the lambda expression’s
enclosing class.

when a lambda expression uses a local variable from its enclosing scope, a
special situation is created that is referred to as a variable capture. In this case, a lambda
expression may only use local variables that are effectively final. An effectively final variable is
one whose value does not change after it is first assigned.

```java
interface MyFunc {
	int func(int n);
}

class VarCapture {
	public static void main(String[] args)
	{
		// A local variable that can be captured.
		int num = 10;
		
		MyFunc myLambda = (n) -> {
			int v = num + n; // legal
			num++;  // illegal as it is modifying
			
			return v;
	};

	System.out.println(myLambda.func(8));
	 
	num = 9; // this is illegal
	// it tries to remove final status
	}
}
```

num is effectively final and can, therefore, be used inside myLambda. This is why the println( ) statement outputs the number 18.

This works because num is not
modified after it is initialized. However, if num were to be modified, either inside the lambda
or outside of it, num would lose its effectively final status. This would cause an error, and the
program would not compile.

It is important to emphasize that a lambda expression can use and modify an instance
variable from its invoking class. It just can’t use a local variable of its enclosing scope unless
that variable is effectively final.

____

#### Throw an Exception from Within a Lambda Expression




___

#### Method References


There is an important feature related to lambda expressions called the method reference.
A method reference provides a way to refer to a method without executing it. It relates to
lambda expressions because it, too, requires a target type context that consists of a compatible
functional interface. When evaluated, a method reference also creates an instance of a functional interface.


##### Method References to static Methods


##### Method References to Instance Methods


#### Constructor References


#### Predefined Functional Interfaces





____
