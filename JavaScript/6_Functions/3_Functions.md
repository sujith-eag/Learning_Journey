
- **Expression**: A fragment of code that produces a value. Expressions can contain other expressions, allowing for nesting.

```js
1;          // Expression
!false;     // Expression
```

- **Statement**: A complete instruction that stands on its own, corresponding to a full sentence. The simplest statement is an expression followed by a semicolon.

```js
1;          // Statement
!false;     // Statement
```

- **Side Effects**: When an expression or statement produces a value but does not affect the program's state or produce a lasting impact (i.e., the value is discarded).

```js
1;          
// No side effect, value is produced and discarded
```

- **Environment**: The collection of bindings (variables) and their values that exist at any given time during the execution of a program. The environment is not empty when a program starts, as it includes built-in values and functions.

---

### Functions in JavaScript

A function is a block of JavaScript code that is defined once but may be executed, or invoked, any number of times.

- **Functions**: A function is essentially a program which is a block of code wrapped in a value. When you assign a function to a variable or pass it as an argument, you are using the function as a value.  

A function can be **invoked**, **called**, or **applied** to run the program inside it.
```js
prompt('Enter detail');        
// Invokes the prompt function

console.log("hello");          
// Invokes the console.log function
```


JavaScript functions are parameterized: a function definition may include a list of identifiers, known as parameters, that work as local variables for the body of the function.

- **Arguments**: The values provided inside the parentheses `()` when invoking a function. These are given to the program inside the function to be used.  
Function invocations provide values, or arguments, for the function’s parameters. Functions often use their argument values to compute a return value.

- **Return Values**: Functions can return values, which are values the function produces when it completes. These returned values can be used in further expressions. The return value becomes the value of the function-invocation expression.

```js
console.log(Math.max(2, 4));   // 4
console.log(Math.min(2, 4) + 100); // 102
```

- **Side Effects of Functions**: Functions like `alert()`, `prompt()`, or `console.log()` often have side effects because they perform actions such as displaying a dialog box or printing to the console.


---

In addition to the arguments, each invocation has another value—the invocation context—that is the value of the `this` keyword.  
If a function is assigned to a property of an object, it is known as a method of that object. When a function is invoked on or through an object, that object is the invocation context or `this` value for the function.

JavaScript functions are closures, meaning they have access to any variables that are in scope where they are defined, even if nested within other functions.

Functions designed to initialize a newly created object are called constructors.

In JavaScript, functions are objects, and they can be manipulated by programs. JavaScript can assign functions to variables and pass them to other functions. You can set properties on them and even invoke methods on them.

---

### Naming Functions

Functions typically represent actions, so their names should usually be verbs. The name should briefly describe what the function does. It's often helpful to start with a prefix that conveys the function's purpose:

- `show...` (e.g., `showMessage()`)
- `get...` (e.g., `getUserInput()`)
- `calc...` (e.g., `calcTotal()`)
- `create...` (e.g., `createElement()`)
- `check...` (e.g., `checkEligibility()`)

- **Clarity**: A function's name should clearly indicate what the function does. If a function performs multiple actions, it might be a good idea to break it into smaller functions. If two functions need to be called together, create a third function that calls both.


---

### **Best Practices**

1. **Keep functions focused**: A function should do exactly what its name implies. If it does more than one thing, consider splitting it into smaller functions.

2. **Avoid repetition**: Functions allow you to structure larger programs by reusing code, so you should use functions to reduce code repetition and isolate different parts of your program.

3. **Organize functions logically**: Group related functions together to make the code more readable and maintainable.

4. **Use descriptive names**: A function's name should give a clear idea of its purpose. Use meaningful and consistent naming conventions throughout your codebase.


---

#18sep24 `06Mar25`

---
