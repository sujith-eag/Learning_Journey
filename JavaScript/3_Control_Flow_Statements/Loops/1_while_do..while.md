The looping statements are those that
bend that path back upon itself to repeat portions of your code. JavaScript has five
looping statements: while, do/while, for, for/of (and its for/await variant), and
for/in.

One common use for loops is
to iterate over the elements of an array

___



### 'while' Loop

Similar to `if` statement which is a basic conditional, the `while` statemet is the basic loop.
The `while` loop executes the code inside its body **as long as** the condition evaluates to **truthy**. The condition is checked **before** each iteration.

```js
while (expression)
	statement
```

```js
initializer / counter variable;
while (condition) {
    // code to run in the loop body
    final-expression;  // increment or other operation
}
```

You can create an infinite loop with the syntax `while(true)`
n expression that starts off truthy would never change, and the loop would never end! 

___

A single execution of the loop body is called an **iteration**.
variable count starts off at 0 and is incremented each time the
body of the loop runs. Once the loop has executed 10 times, the expression becomes false and the while statement finishes.
```js
let count = 0;
while(count < 10) {
	console.log(count);
	count++;
}
```

```js
let number = 0;

while (number <= 12) {
    console.log(number);
    number = number + 2;  // Increment by 2
}
// Output: 0, 2, 4, 6, 8, 10, 12
```

```js
let result = 1;
let counter = 0;

while (counter < 10) {
    result = 2 * result;  // Multiply result by 2 each time
    counter = counter + 1;  // Increment counter
}
console.log(result);  // Output: 1024 (2^10)
```

#### Shortened `while` condition

shorter way to write `while (i != 0)` is  `while(i)`
If the condition is just a variable (e.g., `i`), it can be simplified:

```js
let i = 3;
while (i) {
    alert(i);  // Alert the current value of i
    i--;  // Decrement i
}
// Output: Alerts 3, 2, 1, then stops as i becomes 0
```

```js
let hash = "";  // Start with an empty string

while (hash.length < 7) {
    hash += "#";  // Append one "#" to the string
    console.log(hash);  // Output the current string
}
// Output:
// "#"
// "##"
// "###"
// "####"
// "#####"
// "######"
// "#######"
```

---

### 'do...while' Loop

The do/while loop is like a while loop, except that the loop expression is tested at the
bottom of the loop rather than at the top. This means that the body of the loop is
always executed at least once. The syntax is:
```js
do
	statement
while (expression);
```

The `do...while` loop guarantees **at least one execution** of its body. It first executes the code block, then checks the condition.

```js
initializer / counter variable;
do {
    // code to run in the loop body
    final-expression;  // increment or other operation
} while (condition);
```

```js
let i = 0;
do {
    alert(i);  // Alert the current value of i
    i++;  // Increment i
} while (i < 3);
// Output: Alerts 0, 1, 2
```

**Ensuring user input:**
```js
let yourName;

do {
    yourName = prompt("Who are you?");  // Prompt the user for their name
} while (!yourName);  // Continue if the input is falsy (e.g., empty string)
console.log("Hello " + yourName);  // Output: "Hello <user's name>"
```

In this example, the program will **force** the user to enter a name that isn’t an empty string or `null`. The `!` operator converts the value to a Boolean, and **any non-empty string** is considered **truthy**.

```js
function printArray(a) {
	let len = a.length, i = 0;
	if (len === 0) {
		console.log("Empty Array");
	} else {
		do {
		console.log(a[i]);
		} while(++i < len);
	}
}
```
---

### **Indenting Code**

Although indentation is not required in JavaScript, **proper indentation** makes the code more **readable** for humans. Even though JavaScript can run code in a single line, using proper indentation is a **best practice** to maintain clarity.

**Without indentation:**
```js
if (true != false) {console.log("That makes sense."); if (1 < 2) {console.log("No surprise there.");}}
```

**With proper indentation:**
```js
if (true != false) {
    console.log("That makes sense.");
    if (1 < 2) {
        console.log("No surprise there.");
    }
}
```

---
