#17sep24 

# Values

Chunks of information are called values and Every value has a type that plays a role.
> Numbers, Strings, Boolean, Empty values
___

# Value types / Primitive types 

Called primitive because they can contain only a single thing
String           `let name = "eag";`
Number  `let age = 30;` There's no floating point and normal numbers, all are just numbers.
Boolean        `let isApproved = false;`
Undefined     `let firstName = undefined`   If value is not initialized
null                `let lastName = null;`    intentionally left to be cleared later 

`typeof` operator returns the type of the operand. Used to check the type of a variable,
the types can change based on the value it holds.

`null` is of the type `object`

### Reference types
Object, Array, Function
These can store collection of data and more complex entities.

___

### 1 Empty values

`null`  and  `undefined`  are used to denote the absence of meaningful value. value unknown
These two are values but they do not carry no information. Both are mostly interchangeable.

`null` is used to assign an `empty` or `unkown` value to a variable.

`undefined` is `value is not assigned` as a default initial value for unassigned things.
Many operations yield `undefined` when they have to yield some value if the operation don't produce a meaningful value. 

___

### 2 Numbers

Numerical type values, like 12 13
64 bit memory is used to store a single number value in memory.
Some bits store the negative numbers, some the position of decimal points.

Operators that use two values are called ***binary operators***

Arithmetic
`+  *  -  /  are math operators`
`% are remainder operation` *Modulo operator*
`**` exponentiation

Special Numbers
`Infinity   -Infinity    NaN - not a number`
`0/0 ,  Infinity-Infinity` results in `NaN` which means not a meaningful result.

`Number()` function converts anything passed to it into a number if it can.
```js
const myString = '123';
const myNum = Number(myString);
console.log(typeof myNum);  // number
```

____
### 3 Strings

Text which are enclosed in ` ' '  " "  `` ` quotes.
```js
let str = "Hello";
let str1 = 'single quotes are ok too';

let phrase = `backticks are fine and can embed another ${str}`;
let combined = `${str}${phrase}`;
```

***Template literals*** `${}`  can embed other values
\`\` are extended functionality quotes. they allow us to embed variables and expressions into a string by wrapping them in ${ }.
When something is inside `${ }` is a template literal, its result will be computed, converted to a string and included at that position.
`half of 100 is ${100/2}`
`half of 100 is 50`
Single and double quotes cannot do this embedding functionality.

```js
let name = "john";

console.log( `Hello, ${name}`);
console.log( `the result is ${1+2}`);
```


***escaping character*** means that we do something to make sure they are recognized as text, not part of the code. which is done by putting `\` just before the character. 
Newline can be represented by `backticks \` which is a ***escaping character***.

`\n` represents new line,  `\t` for tab
`\\` ***two back slashes*** are present, they collapse and become a normal character.

```js
First line and\nThis is second line
A newline character is "\n"
A newline character is \"\\n\"

cosnt bigmouth = 'I\'ve got no right to take my place';
```

First and last one is for escaping " "quotes and next two becomes one slash

`+` can be used to ***concatenate strings***
`"con" + "cat" + "e" + "nate"`

`String()` function converts its argument to string.
#### Unary Operators
`typeof` operator produces a string value naming the type of value given.
`console.log(typeof 4.5)`      // number
`console.log(typeof "x")`      // string

___

### 4 Boolean Values

### Comparisons `==  !=  >=  <= `

```js
console.log(3>2);   //true
console.log(3>2);   //false

//Strings can also be compared in same way, 
console.log("Aardvark" < "Zoroaster")   //true
```
When comparing strings `js` goes from left to right comparing each characters Unicode code one by one. So capital is more than small, non-alphabetical characters also included.
The first difference it returns a value. Longer ones are greater than short ones.

_____

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

____

### Strict Comparison  `===`   `!==`

When we do not want any type conversion, there are two more operators
```js
// 0 is seen as false by ==
alert( 0 == false); // true
alert("" == false); // true
// empty string is converted to 0, which is false again

alert("" === false); // false
alert( 0 === false); // false
```
These three character comparison can be used defensively to prevent unexpected type conversion.

___

### Comparison with `null` & `undefined`

When `null` or `undefined` occurs on either side of the operator, it produces true only if both sides are one of `null` or `undefined`
```js
alert(null == undefined);    // true
alert( null === undefined);    // false

alert(null == 0);            // false
```

Useful to test if a value has a real value instead of `null` or `undefined` by comparing it to `null` with the `==` or `!=` operator.
```js
0 == false  // true
"" == false  // true
```

for math comparisons `> < <= >=` `null/undefined` is converted to numbers.
`null` becomes `0`  , `undefined` becomes `NaN`





___

## Objects and Symbols

`object` type is special as they are used to store collection of data and more complex entities.

`symbol` type is used to create unique identities for objects.



Source: Eloquent JavaScript

