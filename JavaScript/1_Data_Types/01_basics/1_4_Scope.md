
The `scope` of a variable is the region of your program source code in which it is defined.

ariables and constants declared with let and const are block scoped. This
means that they are only defined within the block of code in which the let or const
statement appears.

Roughly speaking, if
a variable or constant is declared within a set of curly braces, then those curly braces
delimit the region of code in which the variable or constant is defined


When a declaration appears at the top level, outside of any code blocks, we say it is a
global variable or constant and has global scope. In Node and in client-side JavaScript
modules (see Chapter 10), the scope of a global variable is the file that it is defined in.
In traditional client-side JavaScript, however, the scope of a global variable is the
HTML document in which it is defined.


It is a syntax error to use the same name with more than one let or const declaration
in the same scope. It is legal (though a practice best avoided) to declare a new variable
with the same name in a nested scope

```js
const x = 1;
// Declare x as a global constant
if (x === 1) {
let x = 2;
// Inside a block x can refer to a different value
console.log(x); // Prints 2
}
console.log(x);
// Prints 1: we're back in the global scope now
let x = 3;
// ERROR! Syntax error trying to re-declare x
```



Declarations and types
If you’re used to statically typed languages such as C or Java, you may think that the
primary purpose of variable declarations is to specify the type of values that may be
assigned to a variable. But, as you have seen, there is no type associated with
JavaScript’s variable declarations.2 A JavaScript variable can hold a value of any type.
For example, it is perfectly legal (but generally poor programming style) in JavaScript
to assign a number to a variable and then later assign a string to that variable:
```js
let i = 10;
i = "ten";
```


