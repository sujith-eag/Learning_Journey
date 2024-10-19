# Bindings / Variables

To maintain the internal state, to catch and hold values, `js` provides *bindings* or *variables*

***Restrictions***
No key words and reserved words,
No numbers in the beginning
No space or hyphen ' - ',
No punctuation or special characters except `$ and _`

### Naming things Properly
A variable name should have a clean, obvious meaning, describing the data that it stores.

Some good-to-follow rules are:
* use camelCase for naming things `yourName, squareRoot`
- Use human-readable names like `userName` or `shoppingCart`.
- Stay away from abbreviations or short names like `a`, `b`, and `c`, unless you know what you’re doing.
- Make names maximally descriptive and concise. Examples of bad names are `data` and `value`. 
- If a site visitor is called a “user” then we should name related variables `currentUser` or `newUser` instead of `currentVisitor` or `newManInTown`.
- lazy programmers who, instead of declaring new variables, tend to reuse existing ones. like boxes into which people throw different things without changing their stickers. What’s inside the box now? Who knows?. Such programmers save a little bit on variable declaration but lose ten times more on debugging.

***Comments***
`//` for single line
`/*   */` for multi line comments
______
### `var`
`var`  was old way of declaring variable now removed.


### `let` for Variables
```js
let message:
// If a binding it defined without a value, it gets a value `undefined`
message = 'hello';

let caught = 5*5
```
the key word `let` indicates that this sentence is going to define a binding.
It is followed by the name of that binding and
immediately give it a value by an `=` operator and an expression.

The binding is not tied to that value, it can be disconnected from current value and have them point to a new one; 
```js
let mood = "light"
mood = "dark"
```
`let` is used to create a variable, reassignment do not need it.
Define it with `let` once and then refer to it without `let`.

A single `let` can define multiple bindings, definition must be separated by a comma.

```js
let one = 1, two = 2;

let user = 'John', age = 25, message = "hello";

let user = 'John'
	, age = 25 
	, message = "hello";
```

____

### `const` for Constants

Variables declared using `const` are called constants.
They cannot be reassigned. A value of a constant cannot change, gives error when tried to change.
 ```js
const pi = 3.142;

const myBirthday = '18.04.1999';
```
A constant binding points to the same value as long as it lives.

Some constants are known before hand but some are calculated during runtime but do not change after their initial assignment.
```js
const pageLoadTime = /*Time taken for a webpage to load*/

const age = someCode(myBirthday); // 
```

## Uppercase Constants
Its a practice to use `const` as aliases for difficult to remember values that are known before execution. Named with Capital letters with under scores.
```js
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...when we need to pick a color
let color = COLOR_ORANGE;
alert(color)
```

Redone on #07oct24 
