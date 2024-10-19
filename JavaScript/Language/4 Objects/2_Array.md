#18sep24

# Array

Arrays are special type of objects.
Objects use named indexes and Arrays use numbered indexes.

In `js` used to store sequences of values and is written as a list of values between `[]`

```js
// for creating an empty array:
let arr = new Array();
let arr = [];
```

Can be indexed using the position values.
```js
let listOfNumbers = [2,3,4,5];

console.log(listOfNumbers[2]);  // 4
console.log(listOfNumbers[2-1]);  // 3

const cars = ["Volvo", "BMW", "Tata"];

let car = cars[0];   // car = Volvo
```

```js
const cars = [];
cars[0] = "Volvo";
cars[1] = 'BMW';
```

#### Associative Arrays
Arrays with named indexes are called associative arrays or hashes, but
JavaScript **does not support** arrays with named indexes, it always uses Numbered Index.

If named indexes are used, `js` converts array to an object. Then array methods and properties will produce incorrect result.
```js
const person = [];
person["first"] = "john";
person["last"] = "doe";

person.length;  // 0 wrong
person[0];   // unefined
```



There can be Objects in Array, Functions in Array and Arrays in Array.
#### Array of objects
```js
let journal = [
	{event: ["work", "touched tree", "pizza", "running"],
	squirrel: false},
	
	{event: ["work", "ice cream", "lasagna"],
	squirrel: false},

	{event: ["weekend", "cycling", "peanuts"],
	squirrel: true}
	];
```



## Array Properties and Methods

### Properties

```js
Math.max   myString.length    cars.sort()
```

The length property of an array returns the length of an array (number of array elements).
```js
const fruits = ["Bannana", "Orange", "Mango"];
let len = fruits.length;
let fruit = fruits[0];  // fruit = Bannana
let fruit = fruits[fruits.length-1]; // fruit = Mango
```

The two ways of accessing properties is with a `. or []`
When using `.` dot, the word after the dot is the literal name of the property.
When using `[]` the expression between the brackets are evaluated to get the property name.

## Looping Array Elements

#### Using `for` loop
```js
for (let i=0; i< Journal.length; i++) {
	let entry = Journal[i];
	// Some manipulation
}
```

### `for..of` loop
```js
for (let entry of Journal) {
	conslole.log('${entry.events.length} events.');
}
```
When a `for loop` uses the word `of` after its variable definition, it will loop over the elements of the value given after `of`.
This works for strings and some other data structures.


#### `array.forEach()` method

allows to run a function for every element of the array.
```js
arr.forEach(function(item, index, array) {
	// do something with item
});
```

```js
["Bannana", "Orange", "Mango"].forEach(alert);

const fruits = ["Bannana", "Orange", "Mango"];

fruits.forEach(alert);
// will alert for each item
```

```js
// making a list html item for each item
const fruits = ["Bannana", "Orange", "Mango"];

function myFunction(value) {
	text += "<li>" + value + "</li>";
}

fruits.forEach(myFunction);
```

To elaborate on the position in the array
```js
const fruits = ["Bannana", "Orange", "Mango"];

fruits.forEach( (item, index, array) => {
	alert( `${item} is at index ${index} in ${array}` );
	});

// Bannana is at index 0 in Bannana, Orange, Mango
```



### Function for entry in object

Giving property name `events` is a shorthand that means same thing as `events: events`.
If a property name in brace notation isn't followed by a value, its value is taken from the binding with the same name.
```js
let journal = [];

function addEntry(events, squirrel) {
	journal.push({events, squirrel});
	}

addEntry ( ["work", "touched tree", "pizza", "running"], false);
	
addEntry ( ["work", "ice cream", "lasagna"], false);

addEntry ( ["weekend", "cycling", "peanuts"], true);
```
