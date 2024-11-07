## “unary”, “binary”, “operand”

**An operand** – is what operators are applied to. 
For instance, in the multiplication of `5 * 2` there are two operands: the left operand is `5` and the right operand is `2`. Sometimes, people call these “arguments” instead of “operands”.

 An operator is _unary_ if it has a single operand. For example, the unary negation `-` reverses the sign of a number:  `x = -x;`

An operator is _binary_ if it has two operands. The same minus exists in binary form as well:  `alert (y - x)`


### Operator Precedence

In an expression with many operators, the execution order is defined by their precedence. Each has a precedence number, one with the larger one gets executed first.
If they are same, then the execution is from left to right.
[precedence table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) 

unary plus has precedence 14
addition has precedence 12
assignment operator `=` has precedence 2, so all calculation happens first and then assignment.


#### Modify in place
```js
let n = 2;

n = n+5;
n += 5;

n = n*2;
n *= 2;
```
These modify in place and assign exist for all arithmetic and bitwise operators. `/=   -=`

#### Increment / decrement
increasing or decreasing a number by one, can only be applied to variables.
```js
counter++;
// same as counter += 1;
counter--;

5++; // will give an error
```
'postfix form' `counter++`
'prefix form' `++counter`
both do the same, but There is a difference in what they return.

Postfix form returns the previous value that existed before the increment.
Prefix form returns the incremented form, so if the value needs to be incremented and used immediately, prefix form can be used. 
```js
let counter = 1;
alert( 2 * ++counter); // 4

let counter = 1;
alert( 2 * counter++); // 2   returned onld value
```




## Bitwise operators
[Bitwise Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#bitwise_operators)
Bitwise operators treat arguments as 32-bit integer numbers and work on the level of their binary representation.
These operators are not JavaScript-specific. They are supported in most programming languages.

The list of operators:
- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )

These operators are used very rarely, when we need to fiddle with numbers on the very lowest (bitwise) level. 
