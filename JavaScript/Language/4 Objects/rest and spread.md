https://javascript.info/rest-parameters-spread


Many JavaScript built-in functions support an arbitrary number of arguments.
- `Math.max(arg1, arg2, ..., argN)` – returns the greatest of the arguments.
- `Object.assign(dest, src1, ..., srcN)` – copies properties from `src1..N` into `dest`.

## Rest parameters `...`

(Rest parameters are used to create functions that accept any number of arguments. Used in the parameter of a function to make array.)

A function can be called with as many arguments as possible but it only considers the number of parameters it has assigned.
```js
function sum(a, b) {
	return a + b; }

alert( sum(1, 2, 3, 4, 5));  // 3   excessive are ignored
```

The rest of the parameters can be included in the function definition by using three dots `...` followed by the name of the array that will contain them. 
The dots literally mean “gather the remaining parameters into an array”.

```js
function sumAll(...args) {
	let sum = 0;

	for (let arg of args ) {
		sum += arg;
		}
	return sum;
}
alert ( sumAll(1) );  // 1
alert ( sumAll(1, 2, 3, 4 ));  //10
```

We can choose to get the first parameters as variables, and gather only the rest in an array. The rest parameter `...`must always be at the end.
```js
function showName( first, last, ...titles) {
	alert( first +' '+ last);

	alert( titles[0]);
	alert( titles[1]);
	alert( titles.length );
}

showName( "Julius", "Caesar", "Consul", "Imperator");
```

`rest parameter` is bound to an array containing all further arguments.
```js
function max(...numbers) {
	let result = -Infinity;
	for (let number of numbers) {
		if (number > result) result = number;
		}
	return result;
}

console.log(max(4, 1, 9, -2));    // 9

// using spread syntax in finction call
let numbers = [5, 1, 7];

console.log(max(...numbers));    // 7

console.log(max(9, ...numbers, 2));
```



____________

# Spread syntax

( The spread syntax is used to pass an array to functions that normally require a list of many arguments.
Used in function call as argument to unpack an array)

`rest parameter` is used in function parameter to ***get an array from the arguments***.
`Spread syntax` looks similar, also using `...`, but does quite the opposite.
When `...arr` is used in the ***function call***, it ***“expands” an iterable object*** `arr` into the list of arguments / "expands" an array into its elements..
[Spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) 

```js
// function call, as function argument
myFunction(a, ...iterableObj, b);

// making an array, array literal
[1, ...iterableObj, '4', 'five', 6];

// making an object, object literal
{...obj, key: 'value'}
```

The **spread (`...`)** syntax allows an iterable, such as an array or string, to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected. 

```js
alert( Math.max(3, 5, 1));  // 5

let arr = [3, 5, 1];
alert( Math.max(arr) );  // NaN
// Math.max expects a list of numeric arguments, not an array

alert( Math.max(...arr) ); // 5
// spread turns the array into list of arguments
```

Passing multiple iterables
```js
let arr1 = [1, -2, 3, 4];
let arr2 = [8, 3, -8, 1];

alert( Math.max(...arr1, ...arr2) ); // 8

alert( Math.max(1, 2, ...arr1, 25, 21, ...arr2) ); // 25
```


To ***merge arrays*** or any iterable and to make ***copies***

Square bracket array notation similarly allows triple-dot operator to spread another array into a new array.
```js
let arr1 = [1, -2, 3, 4];
let arr2 = [8, 3, -8, 1];

let arrCopy = [...arr1]; // spreads the array and makes a new array

let merged = [0, ...arr1, 2, ...arr2]; // merging to make a new array
```

```js
let words = ["never", "fully"];

console.log(["will", ...words, "understand"]);

// ["will", "never", "fully", "understand"]
```

```js
const parts = ["shoulders", "knees"];

const lyrics = ["head", ...parts, "and", "toes"];

//  ["head", "shoulders", "knees", "and", "toes"]
```

***In an object***
In an object literal, the spread syntax enumerates the properties of an object and adds the key-value pairs to the object being created.
```js
let obj = { a: 1, b: 2, c: 3};

let objCopy = {...obj};
```
This works even in curly brace objects to add all property from another object. If a property is added multiple times, the last value to be added wins.
```js
let coordinates = {x:10, y:0};
console.log({...coordinates, y:5, z:1})
// {x:10, y:5, z:1}
```


even `for..of` returns characters similarly by iterating.
```js
let str = "Hello";

alert( [...str] ); // H,e,l,l,o   at once

alert( Array.from(str) );  // H,e,l,l,o  
```





Spread syntax can be used when all elements from an object or array need to be included in a new array or object, 
or should be applied one-by-one in a function call's arguments list. 

There are three distinct places that accept the spread syntax:
- [Function arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax#spread_in_function_calls) list (`myFunction(a, ...iterableObj, b)`)
- [Array literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax#spread_in_array_literals) (`[1, ...iterableObj, '4', 'five', 6]`)
- [Object literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax#spread_in_object_literals) (`{ ...obj, key: 'value' }`)





____
