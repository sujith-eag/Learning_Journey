###  numbers

There are two types of numbers, Regular numbers and BigInt numbers.

64 bit memory is used to store a single number value in memory.
Some bits store the negative numbers, some the position of decimal points.

***Arithmetic operators***
```js
+  *  -  /  are math operators
% are remainder operation / Modulo operator
** exponentiation
```
The math operations are safe, sense it will do anything and never stop with a fatal error and die. At worst it will give `NaN` as result.
Operators that use two values are called ***binary operators***


***Special Numbers / Special numeric values***
```js
Infinity   alert(1/0) // Infinity
-Infinity    
NaN // not a number

0/0 ,  Infinity-Infinity results in `NaN`
// which means not a meaningful result.

alert("not a number"/2);  // NaN
alert(NaN +1);  // NaN

// onlt NaN ** 0 is 1 
```
So if there is a `NaN` in the expression it will propagate to the whole result.

### `BigInt`
integers greater than `(253-1)` can’t be stored at all in the “number” type.
`BigInt` type was recently added to the language to represent integers of arbitrary length.

A `BigInt` value is created by appending `n` to the end of an integer:
```js
const bigInt = 12345553213423423424241313322442324234342n;
// the n at the end means it is a BigInt
```


`Number()` function converts anything passed to it into a number if it can.
```js
const myString = '123';
const myNum = Number(myString);
console.log(typeof myNum);  // number
```


### Ways to write a number

```js

let billion = 1000000000;

// using _ as seperator, it gets ignored
let billion = 1_000_000_000;

// shortening the number using 'e' and number of zeroes 
let billion = 1e9;  // i billion

alert( 7.3e9 ); // 7.3 billion

// e multiplies number 1 with zero count, and multiplies it.
```

```js
let mcs = 0.000001;

let mcs = 1e-6;  // five zeroes to left from 1
```