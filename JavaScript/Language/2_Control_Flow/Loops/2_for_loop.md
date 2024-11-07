
# `for` loop

When there is no collection of items to loop through, for loop can be used.
```js
for ( initializer; condition; final-expression; ) {
	// code to run
}
```

Initializer / counter variable
	The first part initializes the loop, usually by defining a binding set to a number. which will be incremented to count the number of times loop has run. 

Condition
	The second part is expression/condition that checks if loop must continue or stop. Generally containing expression with comparison operator to check if the required condition has been met.

Final-expression
	This is always run every time a loop is completed full iteration to update the state of loop. Usually serves to increment or decrement the counter variable to bring it closer to a point where the condition is not true.

The curly braces`{}` that contains the code will be run for each iteration.

```js
for (let number = 0; number <= 12; number = number +2) {
	console.log(number);
}
// 0, 2 ... 10
```
***Inline variable declaration***
The counter variable is declared inside the loop. Such variables are visible only inside the loop. 
```js
let result = 1;

for (let counter = 0; counter < 10; counter = counter + 1) {
	result = result * 2;
}
console.log(result);     // 1024
````

```js
function calculate() {
	for ( let i = 1; i<10; i++) {
		const newResult = '${i} x ${i} = ${i*i}';
		}
}
```

```js
for (const cat of cats) {
	console.log(cat);
}

for (i = 0; i < cats.length; i++) {
	console.log( cats[i] );
}


// to get 'and' before the last cats name.
const cats = ["Lepord", "jaguar", "Tiger", "Lion"];
let myFavouriteCats = "My cats are called ";

for (let i = 0; i < cats.length; i++) {
	if (i === cats.length -1) {
		myFavouriteCats += 'and ${cats[i]}.';
		}
	else {
		myFavouriteCats += '${cats[i]}, ';
		}
}
console.log( myFavouriteCats);
// My cats are called Lepord, jaguar, Tiger, and Lion.
```

***Updating Bindings Succinctly***
```js
counter = counter + 1;    counter += 1;    counter ++;

counter -= 1;   counter --;

result *= 2;
```

___

### Skipping parts

any part of `for` can be skipped.
```js
let i = 0;   // removing beginning
for (; i<3; i++) {
	alert( i );
}
```

```js
let i = 0;
// removing step, makes it similar to while loop
for (; i< 3;) {
	alert( i++);
}
```


______

#### **Chess Board**
```js
let size = 8; // Chessboard size (8x8)
let board = "";

for (let y = 0; y < size; y++) {
    for (let x = 0; x < size; x++) {
        if ((x + y) % 2 === 0) {
            board += " "; // White square
        } else {
            board += "#"; // Black square
        }
    }
    board += "\n"; // Newline after each row
}

console.log(board);
```