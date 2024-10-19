
# Returning a value

***Functions and Side Effects***
Functions are called for their side effect or for their return values.

Functions which returns values are more useful than those that just print, as they can be combined in many ways.
```js
function sum(a, b) {
	return a + b;
}
let result = sum(1, 2);
alert( result ); // 3
```
The directive `return` can be in any place of the function. When execution reaches it, the function stops.

Returning without a value causes the function to exit immediately.
If a function doesn't have a return it is same as returning `undefined`
```js
function showMovie(age) {
	if (!checkAge(age)) {
		return;
		}
	alert( "Showing movie");
	// ..
}
// if checkAge returns false, then it wont proceed.
```


A ***Pure function*** is a specific value producing function that has no side effects and also doesn't rely on side effects from other code. or global bindings whose value might change.




### ***Functions is a Values***
A function binding acts as a name for a specific piece of the program. but both are different.
```js
function sayHi() {
alert( "Hello");
}

alert( sayHi );
```
Here the function wont run because there is no parentheses after `sayHi`.
but will show the content of the function as a string because it is a value.

Since it a value, it is possible to store a function value in new binding, pass it as an argument to function etc.
The binding also, if not constant, be assigned a new value.

```js
function sayHi() {
alert( "Hello");
}
let func = sayHi;
func();
sayHi();
```
Regular values like strings or numbers represent the _data_.
A function can be perceived as an _action_.
We can pass it between variables and run when we want.

____


# Callback functions

Using function as a value. It is passed in as argument without`().

asking a question, if yes, returns true, so `showOk()` as `yes()` gets executed. otherwise `showCancel()` gets executed as `no()`
```js
function ask(question, yes, no) {
	if (confirm(question)) yes()
	else no();
}

function showOk() {
	alert("You agreed.");
	}
function showCancel() {
	alert("You canceled");
	}
	
ask("Do you agree?", showOk, showCancel);
```
**The arguments `showOk` and `showCancel` of `ask` are called _callback functions_ or just _callbacks_.**
The idea is that we pass a function and expect it to be “called back” later if necessary.

```js
function ask(question, yes, no) {
	if (confirm(question)) yes()
	else no();
}

ask( "Do you agree?",
	function() {alert("You agreed.");},
	function() {alert("You canceled");}
	);
```
Here, functions are declared right inside the `ask(...)` call. They have no name, and so are called _anonymous_. 
Such functions are not accessible outside of `ask` (because they are not assigned to variables), but that’s just what we want here.





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



