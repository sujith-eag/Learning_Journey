#18sep24
The concept of wrapping a piece of program in a value has many uses.
It gives us a way to associate names with subprograms, structure larger programs, reduce repetitions, isolate these sub program from each other.


# Naming a function

Functions are actions, so their name should be usually a verb. Describing what function does briefly.
Better to start with a prefix that vaguely describes what it does.
`show..  get..  calc... create.. check..`

A function should do exactly what it is named, if two functions needed to be called then make a third function which calls both.


# Defining a Function


### 1 Function Expression

A function definition is a regular binding and the value of the binding is  a function.
This allows for creating a function in the middle of any expression.

Function expressions are created when the execution reaches them.
```js
const square = function(x) {
	return x * x;
};
console.log(square(12));
// 144
```
Here a `square` is defined to refer to a function that produces the square of a given number.

A function starts with the keyword `function`.
`function` can have a set of `parameters` which are the inputs  and 
`body` in `{}` which contain the statement that are to be executed when the function is called.

Function can have no parameters or multiple parameters.
The `return` keyword determines what gets returned, functions jumps out of function and return the value, if there is no expression before the return, it returns `undefined`.
```js
const makeNoise = function() {
	console.log("Ping!");
};
makeNoise();
// Ping!

const roundTo = function(n, step) {
	let remainder = n % step;
	return n - remainder + (remainder < step/ 2?0 : step);
};
console.log(roundTo(23, 10));
// 20
```
   - If `remainder` is less than half of `step`, it adds `0`, meaning it rounds down to the nearest multiple of `step`.
   - If `remainder` is equal to or greater than half of `step`, it adds `step`, which rounds up to the next multiple of `step`.
##### Python implementation of the same
```python
def makeNoise:
	print ("Ping!")
makeNoise()

def roundTo(n, step):
	remainder = n % step
	if remainder >= step/2:
		return ( (n - remainder) + step)
	return (n - remainder)
print(roundTo(23,10))
```


## 2 Function Declaration

Second way of defining / declaring functions,
Function declaration is created when `js` is preparing to start the script and is visible everywhere.

```js
function square(x) {
	return x * x;
}

//usually
let square = function(x) {
	return x * x;
};
```
When the `function` key word is used at start of statement, it defined the binding `square` and points it at the given function. Doesn't require semicolon after the function.

> Function declarations are not part of regular Top-to-bottom flow of control.
They are conceptually moved to the top of their local scope and can be used by all the code in that scope.
This sometimes offers freedom to order the code in a way that makes sense instead of trying to define all the functions before they are used.

```js
console.log ("The future says: ", future());

function future() {
	return "You will never have flying cars";
}
```

___

### 3 Arrow Functions

Third notation for function which uses `=>` arrow instead of the `function` keyword.
```js
let func = (arg1, arg2,..,argN) => expression;
// is a short hand of function expression
let func = function(arg1, arg2, ..,argN) {
	return expression;
};
```
This creates a `func` that accepts arguments `arg1..` then evaluates the `expression`

```js
let sum = (a, b) => a + b;

const square = (x) => {return x * x;};

const square = x => x * x;
```
The arrow comes after the list of parameters and followed by the function body.
> This input (parameters)  produces this result (the body)

When there is only one parameter, `()` can be omitted.
If body is single expression, rather than a block in braces, that expression will be returned from the function even without `return` statement.

If there are multi line expressions, `{}` curly brace is used for the expression block and a `return` statement has to be given when `{}` is used.
```js
const roundTo = (n, step) => {
	let remainder = n % step;
	return n - remainder;
	};

let sum = (a, b) => {
	let result = a+b;
	return result;
	};
```


When `=>` arrow function doesn't have any parameters, its parameter list is just an empty set of parentheses. `()`,  they must be present
```js
const horn = () => {
	console.log("Toot");
};
```

_____


# Returning a value

***Functions and Side Effects***
Functions are called for their side effect or for their return values.
Functions which returns values are more useful than those that just print, as they can be combined in many ways.
Returning without a value causes the function to exit immediately.
If a function doesn't have a return it is same as returning `undefined`

A ***Pure function*** is a specific value producing function that has no side effects and also doesn't rely on side effects from other code. or global bindings whose value might change.






## The Call Stack

The flow of control has to jump back and forth to the place it was called when it returns, the computer must remember the context from which the call happened.
The place where computer stores this is called the ***call stack***.

Every time a function is called, the current context is stored on top of this stack.
When a function returns, it removes the top context from the stack and uses that context to continue execution.

When the stack grows too big, the computer will fail with 'out of stack space' or 'too much recursion'. Causing Stack Overflow error.

```js
function chicken() {
	return egg();
}
function egg() {
	return chicken();
}

console.log(chicken() + "came first.")
// ???
```

____



## Closure ???
page 46 
The feature of being able to reference a specific instance of a local binding in an enclosing scope is called closure.
A function that references bindings from local scopes around it is called a closure.

```js
function wrapValue(n) {
	let local = n;
	return () => local;
}

let wrap1 = wrapValue(1);
let wrap2 = wrapValue(2);

console.log(wrap1());    // 1
console.log(wrap2());   // 2
```

```js
function multiplier(factor) {
	return number => number * factor;
}

let twice = multiplier(2);
console.log(twice(5));      // 10
```
Multiplier is called and crates an environment in which its `factor` parameter is bound to 2.
The function value it returns, which is stored in `twice`, remembers this environment so that when it is called, it multiplies its argument by 2.  ????


## Recursion

A function call that calls itself is called recursive.

```js
function power(base, exponent) {
	if (exponent == 0){
		return 1;
	} else {
		return base * power(base, exponent - 1);
	}
}
console.log(power(2,3));  // 8
```
This is about three times slower than the version using for loop.
Problems requiring exploring branches are easier with recursion.

#problem 
By starting from the number 1 and repeatedly either adding 5 or multiplying 3, an infinite set of numbers is produced.
How would you write a function that, given a number, tries to find a sequence of such additions and multiplications that produces that number.
```js
function findSolution(target) {
	function find(current, history) {
		if (current == target) {
			return history;
		} else if (current > target) {
			return null;
		} else {
			return find (current + 5, '(${history} + 5)') ??
				find (current * 3, '(${history} * 3)');
			}
		}
		return find (1, "1");
}

console.log(findSolution(24));
	//  (((1 * 3) +5) *3)
```


## Growing Functions

We want to write program that prints two numbers: the number of cows and chickens on a farm, with the words `cows` and `chickens` after them and zeroes padded before both numbers so that they are always three digits long: `007 Cows`

It can be done with two separate functions for each cow and chicken which receive each number separately as arguments, where the number is added with 0 till it is three characters long and then adding that to string "Cow".
So main function will be `printFarmInventory` and within it `cowSring` `chickenString`
but if One more animal has to be added we have to repeat one set of code again.

Better to write the section that makes the string and concatenates separate.

```js
function printZeroPadding(number, label) {
	let numberString = String(number);
	while (numberString.length < 3) {
		numberString = "0" + numberString;
		}
		console.log( '${numberString} ${label}');
}

function printFarmInventory(cows, chickens, pigs) {
	printZeroPadding(cows, "Cows");
	printZeroPadding(chickens, "Chickens");
	printZeroPadding(pigs, "Pigs")
}

printFarmInventory(7, 16, 3);
```


```js
function zeroPad(number, width) {
	let string = String(number);
	while (string.length < width) {
		string = "0" + string;
		}
	return string;
}

function printFarmInventory(cows, chickens, pigs) {
	console.log( '${zeroPad(cows, 3)} Cows');
	console.log( '${zeroPad(chickens, 3)} Chickens');
	console.log( '${zeroPad(pigs, 3)} Pigs')
}

printFarmInventory(7, 16, 3);
```

A useful principle is to refrain from adding cleverness unless absolutely sure it's needed.
It is tempting to write general functions "framework" for everything but resist that urge.
You will be busy writing code that you will never use.



____

# Exercise

Define a function `min` that takes two arguments and returns their minimum.

Write a function `countB` that takes a string as its only argument and returns a number of B characters there are.

Write a function called `countChar` that takes a string and a second argument that indicates the character that has to be counted.



