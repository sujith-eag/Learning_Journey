# `while` and `do...while` loops

## `while`

Similar to `for` loop, the same three parts exist in same order but spread out from keyword.

While `condition` is truthy, the code in `body` executes.
```js
initializer / counter variable
while (condition) {
	// code to run in code body
	final-expression
}
// final expression for incrementing
```
A single execution of the loop body is called an iteration.
```js
let number = 0;

while (number <= 12) {
	console.log(number);
	number = number + 2;
}

// 0  2 ... 10
```

```js
let result = 1;
let counter = 0;

while (counter < 10) {
	result = 2 * result;
	counter = counter + 1;
}
console.log(result);

// 1024  (finding 2 to the power of 10)
```
shorter way to write `while (i != 0)`   is  `while(i)`
```js
let i = 3;
while(i) {
	alert( i);
	i--;
}
```


## `do...while`

a `do` loop always executes its body at least once. 

The loop will first execute the body, then check the condition, whether it should stop only after that first execution as the code comes before the condition.
```js
initializer / counter variable
do {
	// code to run
	final-expression
	} 
while (condition)
```

```js
let i = 0;
do {
	alert(i);
	i++;
} while (i<3);
```

```js
let yourName;

do {
	yourName = prompt("who are you?");
	} while (!yourName);
console.log("Hello" + yourName);
```

This program will force you to enter a name unless it is not an empty string " ".
Applying `!` operator converts a value to Boolean type and all strings except " " convert to true.


***Indenting Code***
is optional in `js`,  the computer will accept the code without them and can even be written in a single line. The indentation makes the code more readable to humans.

```js
if (true != false) {
	console.log("That makes sense.");
	if (1 < 2) {
		console.log("No surprise there.);
		}
}
```
