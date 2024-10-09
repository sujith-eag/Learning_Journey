
Most of the time automatic conversion of values happens by operators and functions to get the right type for their operation.
`alert` converts any value give to a string to show it.
Mathematical operations convert anything into numbers type


#### Automatic Type Conversion

Type Correction happens when comparison is applied to 'wrong' type of value. 
`js` will convert that value to the type it needs using a set of rules, which often are not what you expect or want.
```js
alert('2'>1);  // true
alert('01'==1);  // true

//for Boolean values, true becomes 1 and false 0
alert( true == 1);  // true
alert( false == 0);  // true
```

_________

There are also cases when we need to explicitly convert a value to the expected type.

```js
let theNumber = Number(prompt("Pick a number"));
console.log("Your number is the square root of " + theNumber*theNumber);
```
> `Number  String  Boolean` are used to convert one value type to another as required.


### String Conversion

We can call `String(value)` function to convert a value to a string.

```js
let value = true;

value = String(value);
alert(typeof value); // string
```

### Numeric Conversion

Happens automatically in mathematical operations.
We can use the `Number(value` function to explicitly convert a `value` to a number.
```js
alert( '6' / '2');  // 3

let str = "123";

let num = Number(str);
alert(typeof num);  // number
```
Explicit conversion is needed when reading from a string-based source like a text form.
#### Few common conversion to
If a string is not a valid number then the result will be `NaN`
`undefined` becomes `NaN`
`null` becomes `0`
`true and false` become `1 & 0`


#### Numeric conversion, unary +

The plus `+` exists in two forms: the binary form and the unary form.

The unary plus or, in other words, the plus operator `+` applied to a single value, doesn’t do anything to numbers. 
But if the operand is not a number, the unary plus converts it into a number.
```js
alert( +true );  // 1
alert( +"");  // 0

let apple = "2";
let orange = "3";

alert( apple + orange);  // 23
alert(+apple + +orange);  // 5
```
It actually does the same thing as `Number()` but in short form.

### Boolean Conversion

It is the simplest one.
Happens automatically but can be done explicitly using `Boolean(vlaue)`

The conversion rule is, 
Values that are intuitively `emppty` like 0, " ", `null`, `undeifned`, `NaN`  will become `false`
All other values become `true`

```js
alert( Boolean(1)); // true
alert( Boolean(0)); // false
alert( Boolean("0")); // true
alert( Boolean("")); // false
alert( Boolean(" ")); // true, space is not an empty string
alert( Boolean("Hello")); // true
```
