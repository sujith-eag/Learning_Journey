
## 'for' Loop

The `for` statement simplifies loops that follow a common pattern. Most loops have a counter variable initialized before the loop starts and is tested before each iteration of the loop. Finally, the
counter variable is incremented or otherwise updated at the end of the loop body, just before the variable is tested again. In this kind of loop, the initialization, the test, and the update are the three crucial manipulations of a loop variable.

The `for` loop encodes each of these three manipulations as an expression and makes those expressions as an explicit part of the loop syntax:

```js
for ( initialize ; test ; increment)
	statement


for (initializer; condition; final-expression) {
    // code to run on each iteration
}


initialize;
while(test) {
	statement
	increment;
}
```

The `for` loop is typically used when you know in advance how many times you need to repeat an action. It provides a concise way to initialize, check the condition, and update the loop counter in one line.

The initialize expression is evaluated once, before the loop begins.

The test expression is evaluated before each iteration and controls whether the body of the loop is executed.

Finally, the increment expression is evaluated usually with `++ --` operators.
You can update the loop counter using shorthand operators, these are more concise ways to update variables in loops.
```js
counter = counter + 1; // equivalent to counter++;
counter -= 1;   // equivalent to counter--;
result *= 2;   // equivalent to result = result * 2;
```

____

#### Using 'for' loop

**Simple Loop with Counter**
```js
for(let count = 0; count < 10; count++) {
	console.log(count);
}
// 0, .... , 9
```

```js
for (let number = 0; number <= 12; number = number + 2) {
    console.log(number);
}
// Output: 0, 2, 4, 6, 8, 10, 12
```
`number` starts at 0 and increments by 2 after each iteration, stopping when it exceeds 12.

---

**Loop with a Counter and Calculation**
```js
let result = 1;

for (let counter = 0; counter < 10; counter++) {
    result = result * 2;
}
console.log(result);  // Output: 1024 (2^10)
```

Here, we calculate `2^10` by doubling the result each time, using `counter` as the iteration variable.

Each iteration calculates and prints the square of `i`.
```js
for (let i = 1; i < 10; i++) {
    const newResult = `${i} x ${i} = ${i * i}`;
    console.log(newResult);  // Logs the square of each number
}
```

___

Loops can become a lot more complex than this.
sometimes multiple variables change with each iteration of the loop. This situation is the only place that the comma operator is commonly used in JavaScript; it provides a way to combine multiple initialization and increment expressions into a single expression suitable for use in a for loop:

```js
let i, j, sum = 0;

for(i = 0, j = 10 ; i < 10 ; i++, j--) {
	sum += i * j;
}
```

### **Skipping Parts of the `for` Loop**

Any of the three expressions may be omitted from a `for` loop (initializer, condition, or final-expression), but the two semicolons are required. If you omit the test expression, the loop repeats forever, and `for(;;)` is another way of writing an infinite loop, like while(true).

**Skipping Initializer:**
```js
let i = 0;  // Initializer outside the loop
for (; i < 3; i++) {
    alert(i);  // Output: 0, 1, 2
}
```

**Skipping Final-Expression:**
```js
let i = 0;
for (; i < 3;) {
    alert(i);  // Output: 0, 1, 2
    i++;  // Incrementing inside the loop body
}
```

It is not necessary that loop variable has to be numeric
```js
function tail(o) {  // Return the tail of linked list o

	for(; o.next; o = o.next) /* empty */ ; 
		// Traverse while o.next is truthy
	return o;
}
```

---

#### Adding "and" Before the Last Item in an Array

```js
const cats = ["Lepord", "Jaguar", "Tiger", "Lion"];

let myFavouriteCats = "My cats are called ";

for (let i = 0 ; i < cats.length ; i++) {
    if (i === cats.length - 1) {
        myFavouriteCats += `and ${cats[i]}.`;  // Add "and" before last cat
    } else {
        myFavouriteCats += `${cats[i]}, `;
    }
}
console.log(myFavouriteCats);
// Output: "My cats are called Lepord, Jaguar, Tiger, and Lion."
```

### **Chessboard Pattern**

To print a chessboard pattern, you can use a nested loop:

```js
let size = 8;  // Chessboard size (8x8)
let board = "";  // Start with an empty string

for (let y = 0; y < size; y++) {
    for (let x = 0; x < size; x++) {
        if ((x + y) % 2 === 0) {
            board += " ";  // White square
        } else {
            board += "#";  // Black square
        }
    }
    board += "\n";  // Newline after each row
}

console.log(board);
```

This code generates an 8x8 chessboard pattern using a combination of two loops. Each square is determined by whether the sum of `x` and `y` is even or odd.

---
