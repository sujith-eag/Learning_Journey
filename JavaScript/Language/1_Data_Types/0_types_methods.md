#17sep24 

# Values

Values are Chunks of information and Every value has a type that plays a role.
There are eight basic types
```js
number
bigint
string
boolean
null
undefined
object
symbol
```

___

# Value types

***Primitive Types***
These are Called primitive because they can contain only a single thing
string      `let name = "eag";`
number  `let age = 30;` There's no floating point and normal numbers, all are just numbers.
boolean   `let isApproved = false;`
undefined  `let firstName = undefined`   If value is not initialized
null           `let lastName = null;`    intentionally left to be cleared later 

***Reference types***
Object, Array, Function
These can store collection of data and more complex entities.

`object` type is special as they are used to store collection of data and more complex entities. It is not a primitive type because it can store collections of data.

`symbol` type is used to create unique identities for objects.


___________
### `typeof` operator

`typeof` operator returns the type of the operand. 
Used to check the type of a value, or when we want to handle different type of values differently. 
The types can change based on the value it holds.

```js
typeof 0 // number
typeof 10n // bigint
typeof 'foo' // string
typeof Symbol("id")  // symbol

typeof Math // object
typeof null // object
typeof alert // function
```

The behavior of `typeof` with `null` is wrong here, it is a known error but kept there just for compatibility. `null` is not an object, it is its own type.

The `typeof` operator allows us to see which type is stored in a variable.
- Usually used as `typeof x`, but `typeof(x)` is also possible.
- Returns a string with the name of the type, like `"string"`.


#08oct24

# Methods of primitives

methods are part of objects, primitives are not objects but still `js` allows primitives to be used as objects.
Primitives are not objects.

A primitive
- Is a value of a primitive type.
- There are 7 primitive types: `string`, `number`, `bigint`, `boolean`, `symbol`, `null` and `undefined`.

An object
- Is capable of storing multiple values as properties.
- Can be created with `{}`, for instance: `{name: "John", age: 30}`. There are other kinds of objects in JavaScript: functions, for example, are objects.
Many built-in objects already exist, such as those that work with dates, errors, HTML elements, etc. They have different properties and methods.

### Primitive as an object

1. Primitives are still primitive. A single value.
2. The language allows access to methods and properties of strings, numbers, booleans and symbols.
3. In order for that to work, a special “object wrapper” that provides the extra functionality is created, and then is destroyed.

The “object wrappers” are different for each primitive type and are called: `String`, `Number`, `Boolean`, `Symbol` and `BigInt`. Thus, they provide different sets of methods.

For instance, there exists a string method `str.toUpperCase()` that returns a capitalized `str`.
So primitives can provide methods yet still remain lightweight.

String / Number / Boolean can be used to convert a value to corresponding type.
```js
let num = Number("123");
// converts a string to a number
```

`null` and `undefined` have no corresponding wrapper objects so they have no methods. So they are the most primitive. 
```
```

