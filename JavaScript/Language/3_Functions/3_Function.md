#18sep24

A fragment of code that produces a value is called an *expression*.
Expressions can contain other expressions like nesting.

A JavaScript statement corresponds to a full sentence that stands on its own. Simplest one being an expression with a semicolon after it.
`1;`      `!false;`   these are programs

***Side effects*** are produced when noting actually changes, values are produced and thrown away with no impression.

___

# Functions

The collection of bindings and their values that exist at a given time is called the *environment*. When a program starts, the environment is not empty.

A lot of values provided in the default environment have the type *functions*.
> A function is a program wrapped in a value, such values can be applied in order to run the wrapped program.

Executing a function is called *invoking*, *calling*, *applying*.
`prompt('Enter detail')`
`console.log("hello")`
the values between `()` are called *arguments* are given to the program inside the function.

***Return Values***
When a function produces a value, it is said to `return` that value.
showing dialog box or printing on screen are called `side effects`

```js
console.log(Math.max(2,4)); // 4
console.log(Math.min(2,4) + 100); // 102
```


The concept of wrapping a piece of program in a value has many uses.
It gives us a way to associate names with subprograms, structure larger programs, reduce repetitions, isolate these sub program from each other.


# Naming a function

Functions are actions, so their name should be usually a verb. Describing what function does briefly.
Better to start with a prefix that vaguely describes what it does.
`show..  get..  calc... create.. check..`

A function should do exactly what it is named, if two functions needed to be called then make a third function which calls both.