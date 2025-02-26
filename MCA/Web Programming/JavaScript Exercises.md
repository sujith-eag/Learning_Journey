

**Exercises on 16****th** **April:** Javascript Arrays

1. Declare an array using literal and print the array elements using for loop.
    

Code:

Input:

Output:

1. Declare an array using new constructor and print the array elements using forEach().
    

Code:

Input:

Output:

1. Create an array of numbers and print the Fibonacci series with the help of forEach() method.

```js

let n = pareseInt( prompt("Enter Fib sequence for : "));
let a = 0, b = 1, temp;

document.write("<h2>First" + n + "Fibonacci numbers: </h2>");
document.write("<p>" + a + "," + b + "</p>");

for (let i=2; i<n; i++) {
	temp = a + b;
	document.write("," + temp);
	a=b;
	b = temp
}
```

Code:

Input:

Output:

1. Create an array of numbers and print the sum of numbers with the help of forEach() method.
    

Code:

Input:

Output:

1. Use the Array.forEach() method to copy every element from one array to another.
    

Code:

Input:

Output:

1. Develop a javascript program to demonstrate the concept of arrays and its following
    

methods i)join(), reverse(), sort() and concat().

**Exercises on 19****th** **April:**

1. Front End Application Development.


**Exercises on 22****th** **Mar:** JavaScript I/O

1. Demonstrate the use of Embedded JavaScript to display the following text on your web page.
    

**I am part of the HTML document**!  
This came from my script, and is now on the page!  
_I am also part of the HTML document, after the script results!_

Code:

Input:

Output:

  
  

1. Demonstrate the use of prompt method by accepting user’s name as input.
    

Code:

Input:

Output:

1. Design a simple Web Page to add two input numbers and display their sum using prompt and alert.
    

Code:

Input:

Output:

4. Develop and demonstrate a HTML file that includes Javascript script for the following
    

a) A number n obtained using prompt: The first n Fibonacci numbers using document.write()


b) A number n obtained using prompt: A table from 1 to n and their squares using alert

Code:
```js
let n2 = pasreseInt( prompt("Enter a number for squares table: "));
let sqauresTable = "Numbers\tSquare\n";

for( let i=1; i<=2; i++);
{
	
}
```

Input:

Output:

  
  

**Exercises on 2****nd** **Apr:** JavaScript Functions

5. Find the area of a triangle where lengths of the three of its sides are 5, 6, 7.
    

Code:

Input:

Output:

1. Develop and design JavaScript code to Implement arithmetic operations using functions.
    

Code:

Input:

Output:

1. Develop and design JavaScript Compute GCD and LCM of two numbers using functions.
    
```js
function GCD(a,b)
{
	while(b != 0)
	{
		let temp = b;
		b = a %b;
		a = temp;
	}
	return a;
}
```

```js

```

Code:

Input:

Output:

1. Develop and design JavaScript function to calculate the income of a person
`1000-5000` Commission `10%`
`5001-10000` Commission `15%` 
`10001` and above commission `20%`

```
sales
[45000]
[submit]

Commission: 6670

Salary
```

```js

function calculateIncome(salary)
{
	let commission = 0;
	if (salary >= 1000 && salary <= 5000)
	{
		commission = salary*0.10;
	}
	else if (salary >= 5001 && salary <= 10000)
	{
		commission = salary* 0.15;
	}
	else
	{
		commission = salary * 0.2;
	}
	return comission
}
```

