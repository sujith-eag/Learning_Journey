# Basic Array Methods

Properties that contain functions are called methods of the value they belong to, as in `.toUpperCase` is a method of a string.

```js
// Covered in Previous note of Inserion

length  // gives length of array

// To Add and remove items at end
push()   pop()

// To Add and remove at beginning
shift()  unshift()	

delete()  // makes things undefined

splice() // used to insert, remove, replace elements
toSpliced()
```

```js
at()  // getting element with index

// String to array with delimeted
	split()  join()
	toString()  // array to a comma seperated string
	concat()  // new array including other arrays
	reverse()  // reverses order of array


// extracting parts of array
	slice()  // make new subarray

	
// searching in array
	indexOf()  lastIndexOf()   includes()
	find()  findIndex()  findLastIndex()


copyWithin()  // copy elements to other positions in array
flat()  flatMap()  // flaten multidimensional array
```

__________________________

### arr.at(pos)

`at()` method returns an indexed element from an array. 
similar to `[]` but `[]` does not allow getting the last index using `[-1]`, since `[]` is used for both objects and arrays, `obj[-1]` refers to key -1, not last property of object.
`at()` was introduced to solve this problem.

```js
const fruits = ["Bannana", "Orange", "Mango"];

let fruit = fruits.at(2);  // Mango
let fruit = fruits[2];     // Mango
alert( fruits[-1] );   // error
alert( fruits.at(-1) );  // Mango
```

___

#### str.split(delim)
comma-delimited string of receivers: `John, Pete, Mary`
To get an array of names from this string.

`split()` splits the string into an array by the given delimiter `delim`.
```js
let names = `John, Pete, Mary`;

let arr = names.split(', ');

for (let name of arr) {
	alert( 'A message to ${name}.');
}
```
The `split` method has an optional second numeric argument – a limit on the array length. If it is provided, then the extra elements are ignored.

***Split into letters***
```js
let str = 'test';
alert( str.split('') );  // t, e, s, t
```

_____
### arr.reverse()

The method [arr.reverse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) reverses the order of elements in `arr`.
It also returns the array after the reversal.
```js
let arr = [1, 2, 3, 4, 5];
arr.reverse();

alert( arr );  // 5, 4, 3, 2, 1
```
___

_________________________

## Array to String Conversion

If you
want to save the contents of an array in textual form for later reuse, serialize the array
with JSON.stringify() instead of using the methods described here.

### arr.join(glue)

The call [arr.join(glue)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) does the reverse to `split`. 
It converts an array to a string and concatenates them, returning the resulting string of `arr` items joined by `glue` between them.

`join()` method allows joining all array elements into a string similar to `toString` but the separator glue can be assigned.
```js
const arr = ["Bannana", "Orange", "Mango"];

let str = arr.join(" * ");  // Bannana * Orange * Mango

let str = arr.join(';');  // glue the array into string using string using ;
alert(str);  // Bannana;Orange;Mango
```

```js
let a = [1,2,3];
a.join()   // "1,2,3"

a.join(" ")  // "1 2 3"
a.join("")  // "123"

let b = new Array(10);
b.join("-")  // "--------" a string of 9 hyphens
```

### toString()

Like all JavaScript objects, arrays have `toString()` method, Converting an Array to String of comma separated values. This is an automatic process when an outputting an array. 

For an array this works like the `join()` method with no arguments 
```js
const fruits = ["Bannana", "Orange", "Mango"];

fruits.toString();  // Bannana,Orange,Mango

alert(fruits) // same as above
```

```js
[1,2,3].toString()
// => "1,2,3"
["a", "b", "c"].toString() // => "a,b,c"
[1, [2,"c"]].toString()
// => "1,2,c"
```


_____________
