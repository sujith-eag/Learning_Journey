

In computer science, recursion is a method of solving a computational problem where the solution depends on solutions to smaller instances of the same problem.

#### Recursion properties
• The primary property of recursion is the ability to solve a problem by breaking it
down into smaller sub-problems, each of which can be solved in the same way.
• A recursive function must have a base case or stopping criteria to avoid infinite
recursion.
• Recursion involves calling the same function within itself, which leads to a call stack.
• Recursive functions may be less efficient than iterative solutions in terms of memory
and performance.

#### APPLICATIONS OF RECURSION
Recursion is used in many fields of computer science and mathematics, which includes:
• Searching and sorting algorithms: Recursive algorithms are used to search and sort data
structures like trees and graphs.
• Mathematical calculations: Recursive algorithms are used to solve problems such as factorial, Fibonacci sequence, etc.
• Compiler design: Recursion is used in the design of compilers to parse and analyze
programming languages.
• Graphics: many computer graphics algorithms, such as fractals and the Mandelbrot set, use recursion to generate complex patterns.
• Artificial intelligence: recursive neural networks are used in natural language processing,
computer vision, and other AI applications.


#### Designing the recursive functions
Recursive solution - Not all problems can be solved using recursive. Problem that can be solved using recursive is a problem that can be solved by breaking the problem into smaller instances of problem, solve and combine.

Key Concepts of recursion process
1. Base Case: This is the condition at which the recursion process stops. Without a base case, the function would call itself indefinitely, leading to a stack overflow.
2. Recursive Case: This part of the function calls itself with a modified argument, moving towards the base case.

Rules for designing recursive algorithm:
• Determine the base case - There are one or more terminal cases whereby the problem will be solved without calling the recursive function again.
• Determine the general case – recursive call by reducing the size of the problem.
• Combine the base case and general case into an algorithm.



#### Factorial of a number

BASE CASE:
```c
if (n == 0) {
return 1;
}
```
Recursive Case:
```c
return n * factorial(n - 1);
```
For a positive integer n, the function calls itself with the argument n - 1 and multiplies the result by n.
Example Output:
Let’s say we call factorial(4):
1.factorial(4) calls factorial(3)
2.factorial(3) calls factorial(2).
3.factorial(2) calls factorial(1).
4.factorial(1) calls factorial(0).
5.factorial(0) returns 1 (base case).
6.factorial(1) returns 1 * 1 = 1.
7.factorial(2) = 2 * factorial(1) = 2*1 = 2
8.factorial(3) = 3 * factorial(2) = 3*2 = 6
9.factorial(4) = 4 * factorial(3) = 4*6 = 24


##### Factorial without Recursion
```c
#include<stdio.h>
int main()
{
int i,f=1, num;
printf("Enter a number: ");
scanf("%d", &num);
for(i=1;i<=num;i++)
f = f * i;
printf("%d! = %d\n", num, f);
return 0;
}
```



```c
#include <stdio.h>
// A recursive function to calculate factorial FACTORIAL WITH
int factorial(int n)
RECURSION
{
	if (n == 0)
	{
	return 1; // Base case
	}
	else
	{ //function calling itself with modified argument
	return n * factorial(n - 1);
	}
}
int main()
{
	int num; // Prompt user to enter a number
	printf("Enter a non-negative integer: ");
	scanf("%d", &num); //store the number in num // Validate the input.
	if (num < 0)  // number is non-negative.
	{
		printf("Factorial is calculated for negative numbers.\n");
	}
	else
	{ // Calculate and print the factorial for input number
		printf("Factorial of %d is %d\n", num, factorial(num));
	}
	return 0;
}
```

