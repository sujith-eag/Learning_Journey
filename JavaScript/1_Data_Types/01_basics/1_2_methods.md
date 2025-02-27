
## Methods of Primitives

JavaScript supports an object-oriented programming style. This means that
rather than having globally defined functions to operate on values of various types,
the types themselves define methods for working with values. 

To sort the elements of
an array `a`, we don’t pass `a` to a `sort()` function. Instead, we invoke the
`sort()` method of `a`:
```js
a.sort();
// The object-oriented version of sort(a).
```

Technically, it is only JavaScript objects
that have methods. 

numbers, strings, boolean, and symbol values behave as if they have methods. 

In JavaScript, null and undefined are the only values that methods cannot be invoked on.

While primitives (like strings, numbers, booleans) are not objects by themselves, JavaScript allows them to **behave like objects** in certain situations. This is done through **"wrapper objects"** that temporarily convert the primitive to an object for method access.

When you call a method on a primitive value, JavaScript **wraps** the primitive in an appropriate **object wrapper** (e.g., `String`, `Number`, `Boolean`, `Symbol`, or `BigInt`). After the method call, the wrapper is discarded.

```js
let str = "hello";
console.log(str.toUpperCase());  // "HELLO"
```
- `str` is a primitive string.
- JavaScript temporarily wraps it in a `String` object to call the `toUpperCase` method, and then the wrapper is discarded. So primitives can provide methods yet still remain lightweight.

### Wrappers for Each Primitive Type:
- **String** has methods like `.toUpperCase()`, `.toLowerCase()`, etc.
- **Number** has methods like `.toFixed()`, `.toPrecision()`, etc.
- **Boolean** has methods like `.toString()` to convert it into a string.

However, **`null`** and **`undefined`** do not have object wrappers, so they **cannot** be used with methods.

#### Converting primitive types:
```js
let num = Number("123"); // Converts the string "123" into a number
let booleanVal = Boolean(0); // Converts 0 to false
```

> **Note**: `null` and `undefined` do not have methods because they are **the most primitive types** and do not have associated object wrappers.

---

- **Primitive types**: Single values, immutable, include `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`.
- **Reference types**: Store collections of data and more complex entities, include `object`, `array`, `function`, etc.
- **`typeof` operator**: Used to check the type of a value.
- **Wrapper objects**: Allow primitives to behave like objects when methods are invoked on them (e.g., `String`, `Number`, `Boolean`).

---

### Empty values

`null` is used to assign an `empty`, `nothing` or `value unkown` value to a variable.

`undefined` means `value is not assigned` 
It as a default initial value when variable is declared but value is not assigned.
Many operations yield `undefined` when they have to yield some value if the operation don't produce a meaningful value. 


`null`  and  `undefined`  are used to denote the absence of meaningful value / value unknown.
These two are values but they do not carry no information. Both are mostly interchangeable.


___
