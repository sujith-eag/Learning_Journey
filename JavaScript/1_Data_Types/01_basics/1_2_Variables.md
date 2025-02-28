When a program
needs to retain a value for future use, it assigns the value to (or “stores” the value in) a
variable. Variables have names, and they allow use of those names in our programs to
refer to values


In JavaScript, *bindings* (also known as *variables*) are used to maintain the internal state and store values.

he term “variable” implies that
new values can be assigned: that the value associated with the variable may vary as
our program runs. If we permanently assign a value to a name, then we call that name
a constant instead of a variable.

____


## Rules for naming variables:

- **No keywords or reserved words** (e.g., `if`, `for`, `function`, etc.).
- **Cannot start with a number** (e.g., `123variable` is invalid).
- **No spaces or hyphens (`-`)**.
- **No special characters**, except for `$` and `_`.

---

## Naming Variables Properly

A good variable name should be **descriptive** and **easy to understand**. It should clearly represent the value or data that it holds.

- **Use `camelCase`** for variable names (e.g., `userName`, `squareRoot`, `fuzzyLittleTurtle`).
- Choose **human-readable names** that describe the purpose of the variable (e.g., `currentUser`, `shoppingCart`).
- **Avoid abbreviations or short names** like `a`, `b`, and `c`, unless it's clear what they represent.
- **Be descriptive** but also **concise**. For example, avoid overly generic names like `data` or `value`.
- If referring to a user in your application, use names like `currentUser` or `newUser` instead of vague terms like `currentVisitor` or `newManInTown`.
- lazy programmers who, instead of declaring new variables, tend to reuse existing ones. like boxes into which people throw different things without changing their stickers. What’s inside the box now? Who knows?. Such programmers save a little bit on variable declaration but lose ten times more on debugging.

```js
// Descriptive variable names
let userName = 'Jane Doe';
let totalPrice = 100.50;
```
___

## 'var' (old Way of Declaring Variables)

The `var` keyword was previously used to declare variables in JavaScript, but it is now considered outdated due to some issues with variable scoping. As such, its usage is discouraged in favor of `let` and `const`.

---

## 'let' for Declaring Variables

The `let` keyword is used to declare variables that can be **reassigned** later.
If you don’t specify an initial value for a variable with the let statement, the variable
is declared, but its value is undefined until your code assigns a value to it.
```js
let i;
let sum;

let i, sum;
```

Once a variable is declared with `let`, it can be reassigned, but it does **not** need `let` for the reassignment. You only use `let` when declaring the variable for the first time.
```js
let message; // Declaring a variable
message = 'Hello'; // Assigning a value

let i = 0, j = 0, k = 0;

let x = 2, y = x*x;
// Initializing using previous variables

// Spliting the declarations across multiple lines:
let user = 'John'
    , age = 25
    , message = 'Hello';
```

The binding is not tied to that value, it can be disconnected from current value and have them point to a new one;
```js
let mood = 'light';  // Initial assignment
mood = 'dark';       // Reassigning the value
```


---

## 'const' for Constants

The `const` keyword is used to declare **constants**. Once a value is assigned to a `const` variable, it **cannot be reassigned**. Attempting to change the value of a constant results in `TypeError`.

```js
const pi = 3.142;          // Constant value
const myBirthday = '18.04.1999';  // Another constant
```
A constant binding points to the same value as long as it lives. **Constants cannot be reassigned** once their initial value is set.

Use const only for values that are fundamentally unchanging, like physical constants, program versions, byte sequence etc.

A common convention for constants is to use **uppercase letters** with underscores (`_`) to separate words. This makes them easier to identify in your code.

```js
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// Using the constant to set a variable
let color = COLOR_ORANGE;
alert(color);  // Outputs the color value
```

### Constants and Runtime Values:
Some constants may be known beforehand (e.g., `pi`), while others are calculated at runtime but remain unchanged after their initial assignment.

```js
const pageLoadTime = /* Time taken for a webpage to load */;

const age = calculateAge(myBirthday); // Value computed at runtime
```

---

Loops includes a loop variable that gets a new value assigned to it
on each iteration of the loop. JavaScript allows us to declare the loop variable as part of the loop syntax itself, and this is another common way to use let:
```js
for(let i = 0, len = data.length; i < len; i++) console.log(data[i]);
for(let datum of data) console.log(datum);
for(let property in object) console.log(property);
```
It may seem surprising, but you can also use const to declare the loop “variables” for for/in and for/of loops, as long as the body of the loop does not reassign a new value. In this case, the const declaration is just saying that the value is constant for the duration of one loop iteration:

```js
for(const datum of data) 
	console.log(datum);

for(const property in object) 
	console.log(property);
```
___

### Destructuring Assignments

When a destructuring assignment occurs, one or more values are
extracted (“destructured”) from the value on the right and stored into the variables
named on the left.

```js
let [x,y] = [1,2];
[x,y] = [x+1,y+1];
[x,y] = [y,x];
[x,y]
// Same as let x=1, y=2
// Same as x = x + 1, y = y + 1
// Swap the value of the two variables
// => [3,2]: the incremented and swapped values
```

ES6 implements a kind of compound declaration and assignment syntax known as
destructuring assignment. In a destructuring assignment, the value on the righthand
side of the equals sign is an array or object (a “structured” value), and the lefthand
side specifies one or more variable names using a syntax that mimics array and object
literal syntax.


destructuring assignment makes it easy to work with functions that
return arrays of values:
```
// Convert [x,y] coordinates to [r,theta] polar coordinates
function toPolar(x, y) {
return [Math.sqrt(x*x+y*y), Math.atan2(y,x)];
}

// Convert polar to Cartesian coordinates
function toCartesian(r, theta) {
return [r*Math.cos(theta), r*Math.sin(theta)];
}

let [r,theta] = toPolar(1.0, 1.0); // r == Math.sqrt(2); theta == Math.PI/4
let [x,y] = toCartesian(r,theta);
// [x, y] == [1.0, 1,0]
```



The number of variables on the left of a destructuring assignment does not have to
match the number of array elements on the right. Extra variables on the left are set to
undefined, and extra values on the right are ignored.

```js
> let [x,y]=[1]
> x
1
> y
undefined
> [x,y]
[ 1, undefined ]


> [x,y] = [1,2,3]
[ 1, 2, 3 ]
> [x,y]
[ 1, 2 ]
```

The list of variables on the left
can include extra commas to skip certain values on the right:
```js
> [ , x, , y] = [1,2,3,4]
[ 1, 2, 3, 4 ]
> [x, y]
[ 2, 4 ]
```


If you want to collect all unused or remaining values into a single variable when
destructuring an array, use three dots (...) before the last variable name on the left-
hand side:
```
let [x, ...y] = [1,2,3,4]; // y == [2,3,4]
```






---

Redone on #07oct24 `28Feb25`

---
