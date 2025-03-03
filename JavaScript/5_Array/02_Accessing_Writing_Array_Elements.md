

You access an element of an array using the `[]` operator.

Array elements can be accessed using their index values. Arrays are **zero-indexed**. You can also use arithmetic expressions as indices.
An arbitrary expression that has a non-
negative integer value should be inside the brackets. You can use this syntax to both
read and write the value of an element of an array.

```js
const cars = ["Volvo", "BMW", "Tata"];
let car = cars[0];  // "Volvo"
```

```js
const cars = [];
cars[0] = "Volvo";
cars[1] = 'BMW';
```

```js
let a = ["world"];    // Starts with one-element array

let value = a[0];    
// Read element 0, and store value

a[1] = 3.14;   
// Write element 1

let i = 2;
a[i] = 3;   // Write element 2

a[i + 1] = "hello";  // write element 3  

a[a[i]] = a[0];     
// Read elements 0 and 2, write element 3
```


_____

Remember that arrays are a specialized kind of object. The square brackets used to
access array elements work just like the square brackets used to access object proper‐
ties. JavaScript converts the numeric array index you specify to a string—the index 1
becomes the string "1"—then uses that string as a property name. There is nothing
special about the conversion of the index from a number to a string: you can do that
with regular objects, too:
```js
let o = {};
// Create a plain object
o[1] = "one"; // Index it with an integer
o["1"]
// => "one"; numeric and string property names are the same
```
It is helpful to clearly distinguish an array index from an object property name. All
indexes are property names, but only property names that are integers between 0 and
`2^32` are indexes.




Note that you can index an array using numbers that are negative or that are not inte‐
gers. When you do this, the number is converted to a string, and that string is used as
the property name. Since the name is not a non-negative integer, it is treated as a reg‐
ular object property, not an array index. Also, if you index an array with a string that
happens to be a non-negative integer, it behaves as an array index, not an object prop‐
erty. The same is true if you use a floating-point number that is the same as an
integer:
```js
a[-1.23] = true;
// This creates a property named "-1.23"

a["1000"] = 0;  // This the 1001st element of the array

a[1.000] = 1; // Array index 1. Same as a[1] = 1;
```


The fact that array indexes are simply a special type of object property name means
that JavaScript arrays have no notion of an “out of bounds” error. When you try to
query a nonexistent property of any object, you don’t get an error; you simply get
undefined. This is just as true for arrays as it is for objects:
```js
let a = [true, false]; // This array has elements at indexes 0 and 1
a[2]
// => undefined; no element at this index.
a[-1]
// => undefined; no property with this name.
```

---


### **Looping Through Arrays**

#### 1. **`for` Loop**

A traditional `for` loop is a common way to iterate through an array:

```js
for (let i = 0; i < journal.length; i++) {
  let entry = journal[i];
  console.log(entry);  // Do something with each entry
}
```

Copying to a new array
```js
let a = ["a", "b", "c"];
let b = [];

for( let i =0;  i< a.length; i++)
{
	b[i] = a[i];
}

// in ES6, copy arrays with Array.from()
let c = Array.from(b);
```


if we want to compare two distinct objects or arrays, we must compare their properties or elements.
```js
function equalArrays(a, b) 
{
	if (a === b) return true;
	// Identical arrays are equal
	if (a.length !== b.length) return false; 
	// Different-size arrays not equal

	for(let i = 0; i < a.length; i++) 
	{
		// Loop through all elements
		if (a[i] !== b[i]) return false;
		// If any differ, arrays not equal
	}
	return true;
}
```

#### 2. **`for..of` Loop**

The `for..of` loop is a simpler way to iterate over array elements. It gives you the value directly without needing the index.

```js
for (let entry of journal) {
  console.log(`${entry.event.length} events.`);  // logs the number of events
}
```

#### 3. **`forEach()` Method**

The `forEach()` method allows you to run a function for each item in the array:

```js
arr.forEach(function(item, index, array) {
	// do something with item
});
```

```js
["Banana", "Orange", "Mango"].forEach(alert);
// This will alert each fruit in the array

const fruits = ["Bannana", "Orange", "Mango"];
fruits.forEach(alert);
```

```js
// making a list html item for each item
const fruits = ["Bannana", "Orange", "Mango"];

function myFunction(value) {
	text += "<li>" + value + "</li>";
}

fruits.forEach(myFunction);
```

You can also access the current index and the full array within the callback function:

```js
fruits.forEach((item, index, array) => {
  alert(`${item} is at index ${index} in ${array}`);
});
```

---

### **Using Functions to Manipulate Array Data**

JavaScript provides several ways to work with arrays and manipulate their data.

#### 1. **Function for Adding Entries to an Array**

If you want to simplify adding entries to an array of objects, you can use a function:

```js
let journal = [];

function addEntry(events, squirrel) {
  journal.push({events, squirrel});
}

addEntry(["work", "touched tree", "pizza", "running"], false);
addEntry(["work", "ice cream", "lasagna"], false);
addEntry(["weekend", "cycling", "peanuts"], true);
```

This is a shorthand for creating an object with properties named `events` and `squirrel`. Since the property names match the argument names, JavaScript will automatically assign them.

---

### **Summary of Key Points**

- **Arrays in JavaScript** are ordered lists of values, indexed by numbers.
- Arrays are **not associative arrays** (i.e., they cannot use string keys without being converted into objects).
- You can create arrays using both the array literal (`[]`) and the `Array` constructor (`new Array()`).
- **Array properties and methods** like `length`, `forEach()`, and `push()` are essential for manipulating data.
- JavaScript arrays can store **different data types**, including objects, functions, and even other arrays.
- **Iterating through arrays** can be done with `for` loops, `for..of`, and `forEach()` methods, each offering different levels of control and readability.


