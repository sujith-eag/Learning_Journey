
# Expressions and Statements

A fragment of code that produces a value is called an *expression*
Expressions can contain other expressions like nesting.

A JavaScript statement corresponds to a full sentence that stands on its own. Simplest one being an expression with a semicolon after it.
`1;`      `!false;`   these are programs

***Side effects*** are produced when noting actually changes, values are produced and thrown away with no impression.

___

# Functions

The collection of bindings and their values that exist at a given time is called the *environment*. When a program starts, the environment is not empty.

A lot of values provided in the default environment have the type *functions*.
> A function is a program wrapped in a value, such values can be applied in order to run the wrapped program.

Executing a function is called *invoking*, *calling*, *applying*.
`prompt('Enter detail')`
`console.log("hello")`
the values between `()` are called *arguments* are given to the program inside the function.

***Return Values***
When a function produces a value, it is said to `return` that value.
showing dialog box or printing on screen are called `side effects`

`console.log(Math.max(2,4));`    4
`console.log(Math.min(2,4) + 100);`   102

___


# Control Flow

```js
let theNumber = Number(prompt("Pick a number"));
console.log("Your number is the square root of " + theNumber*theNumber);
```
> `Number  String  Boolean` are used to convert one value type to another as required.


## Conditional Execution

### `if`

When we want some code to run if and only if some condition holds using Boolean expression.
```js
if (hour < 18) {
	greeting = "Good Day";
}

// to show the square input only if the input is actually a number.

let theNumber = Number(prompt("pick a number"));

if (!Number.isNaN(theNumber)) {
	console.log("Your number is square root of " + theNumber*theNumber);
}
```

The `Number` function returns `Nan` if its a string that does not represent a number.
`Number.isNaN` is a standard function that returns true only if the argument is `NaN`.
so  'unless `theNumber` is not-a-number, do this'

The statement after the `if` wrapped in `{}` is used to group any number of statements into a single statement called block.
They can be avoided for just one statement
` if (1+1 == 2) console.log("It's true");`     

_____

### `else` 

`else` is used to create an alternate path when the `if` condition is not true.
```js
let theNumber = Number(prompt("Pick a number"));

if (!Number.isNaN(theNumber)) {
	console.log("Your number is the square of " + theNumber*theNumber);
} else {
	console.log("why didn't you give me a number?");
}
```

### `else if`

When there are more than two paths, if / else can be chained together
```js
let num = Number(prompt("Pick a number"));

if (num < 10) {
	console.log("Small");
} else if (num < 100) {
	console.log("Medium");
} else {
	console.log("Large");
}
```

`if` number is less than 10, prints small and is done. 
if it isn't, then takes `else` branch which contains a second `if`,
if that isn't, moves to next `else` block.

_______

## `switch` statements   `switch()  case x:  default:`

They take a single expression or value as an input, and then look through several choices until they find one that matches that value, executing the corresponding code that goes along with it.
A common code format is
```js
if (x == "value1") action1();
else if (x == "value2") action2();
else if (x == "vlaue3") action();
else defaultAction();
```

```js
switch (expression) {
	case choice1: 
		//run this code
		break;
	case choice2:
		// run this code
		break;
	default:
		// if none matched, just run this code
		break;
}
```

```js
switch (prompt("What is the weather like?")) {
	case "rainy":
		console.log("Remember to bring an umbrella.");
		break;
	case "sunny":
		console.log("Dress lightly.");
		break;
	case "cloudy":
		console.log("Go, outside.");
		break;
	default:
		console.log("Unkown weather type!");
		break;
}
```

As many number of `case` can be put inside the block opened by `switch`.
The program will start executing at the label that corresponds to the value that `switch` was given, or at `default` if no matching value is found.

If there is no `break` statement it will continue executing across other labels.


____


Source: Eloquent JavaScript


#### Making 7 hash
```js
let hash = null;

while (hash.length < 7) {
	hash + "#";
	console.log(hash);
}
```

#### Fizz Buzz
```js
for (let number = 1; if number < 100; number += 1) {
	if ((number%3) === 0 && (number%5) === 0) {
		console.log("fizzbuzz");
		}
	else if ( (number%5) === 0) {
		console.log("buzz");
		}
	else if ( (number%3) === 0) {
		console.log("fizz");
		}
	else {
	console.log(number)
		}
}
```

#### Chessboard
