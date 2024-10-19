
### `break`
The `break` statement has the effect of immediately jumping out of the enclosing loop. forcing the exit.

Finding a number that is greater than or equal to 20 and divisible by 7
```js
for (let current = 20; current = current + 1) {
	if (current % 7 == 0) {
	console.log(current);
	break;
	}
}
// 21
```

```js
let sum = 0;

while(true) {
	let value = +prompt("Enter a number", '');

	if (!value) break;  // break if empty line

	sum += value;
}
alert( 'sum: ' + sum );
```

### `continue`

`continue` influences the the progress of a loop. 
when `continue` is enclosed in a loop body, control jumps stops executing the code in the loop, jumps out of the body and continues with the next iteration of the loop.
```js
for (let i = 0; i<10; i++) {
	if (i%2 == 0) continue;
	alert(i);  //  1, 3, 5, 7, 9
}
```
Continue not allowed with ternary `?`

___________

### Labels for `break/continue`

To break out of multiple loops at once.
A label is an identifier with a colon before a loop;
```js
labelName: for (...){
	...
	}

labelName:
for (...){
	...
	}
```

The `break labelName` breaks out of the named loop.
```js
outer:  // placing the label
for (let i = 0; i < 3; i++) {
	for (let j = 0; j < 3; j++) {
		let input = prompt ( 'value at coords (${i},${j})' ) , '' );
	// if an empty string or cancelled, then break out of both loops
	if (!input) break outer;
		}
}
alert ('Done!');
```
The `continue` directive can also be used with label, which continues to the next iteration of the labeled loop.

A `break` directive must be inside the code block
```js
label: {
	// ...
	break label; 
	// ...
}
```