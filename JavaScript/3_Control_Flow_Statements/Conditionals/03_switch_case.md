
## 'switch' Statements

The `switch` statement is a more concise and readable way to handle multiple conditional checks based on a single value. It is often used as an alternative to multiple `if...else if` statements, particularly when you have many conditions to check against a single expression but not multiple conditional checks.

```js
switch (expression) {
    case value1:
        // code to execute if expression === value1
        break;
    case value2:
        // code to execute if expression === value2
        break;
    default:
        // code to execute if no cases match
        break;
}
```
The switch keyword is followed by an expression in parentheses and a block of code in curly braces.
Various
locations in the block of code are labeled with the case keyword followed by an
expression and a colon. When a switch executes, it computes the value of expression
and then looks for a case label whose expression evaluates to the same value (where
sameness is determined by the === operator, expressions must match without any type conversion `"3" !== 3` ). 

If it finds one, it starts executing the
block of code at the statement labeled by the case. If it does not find a case with a
matching value, it looks for a statement labeled default:. If there is no default:
label, the switch statement skips the block of code altogether.

* Execution continues till the nearest `break`, or end of `switch`.
* If there is no `break` ***then the execution continues with the next `case` without any checks***
he break state‐
ment, causes the interpreter to jump to the end (or
“break out”) of the switch statement and continue with the statement that follows it.
The case clauses in a switch statement specify only the starting point of the desired
code; they do not specify any ending point. In the absence of break statements, a
switch statement begins executing its block of code at the case label that matches the value of its expression and continues executing statements until it reaches the end of
the block.

**Fall through**
On rare occasions, it is useful to write code like this that “falls through”
from one case label to the next, but 99% of the time you should be careful to end
every case with a break statement. 

When using switch inside a function, however,
you may use a return statement instead of a break statement. Both serve to terminate
the switch statement and prevent execution from falling through to the next case.


---


```js
let a = 2 + 2;

switch (a) {
    case 3:
        alert('Too small');
        break;
    case 4:
        alert('Exactly');
        break;
    default:
        alert('I don’t know such values');
}
```

`a` matches `case 4`, so the corresponding code `alert('Exactly')` is executed.
The `break` statement prevents further case evaluation, exiting the `switch` block.

```js
function convert(x) {
	switch(typeof x) {
		case "number":  // Convert to a hexadecimal integer
			return x.toString(16);
		case "string":  // Return the string enclosed in quotes
			return '"' + x + '"';
		default:     // Convert any other type in the usual way
			return String(x);
	}
}
```

---

### **Weather Application**

```js
switch (prompt("What is the weather like?")) {
    case "rainy":
        console.log("Remember to bring an umbrella.");
        break;
    case "sunny":
        console.log("Dress lightly.");
        break;
    case "cloudy":
        console.log("Go outside.");
        break;
    default:
        console.log("Unknown weather type!");
        break;
}
```


---

### Grouping 'case' Blocks

You can group multiple `case` values that should run the same code. This allows you to combine cases that share identical behavior.

```js
let a = 3;

switch(a) {
    case 4:
        alert('Right!');
        break;

    case 3:
    case 5:
        alert('Wrong');
        alert("Why don't you take a math class?");
        break;

    default:
        alert('The result is strange.');
}
```

---

### **Key Points to Remember**

1. **`switch` uses strict equality (`===`)**: Ensure that both the value and type match. For example, `'3' !== 3`.
2. **`break` is optional**: Without it, execution will "fall through" to the next `case`.
3. **`default` is optional**: It provides a fallback when no cases match.
4. **Many `case` values can share the same block**: You can group cases that should execute the same code.
5. **`switch` is generally more readable**: When dealing with many conditions based on a single value, `switch` can improve readability compared to long chains of `if...else` statements.

---
