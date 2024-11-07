
# `for..in` loop
- [for…in](https://javascript.info/object#forin) to loop and walk over keys / properties of an object.

### `in` operator
`in` operator is used to check the existence of a property in an object. Is useful because there will be no error if trying a access a property that doesn't exist in an object (returns `undefined')
```js
let user = {};
alert( user.noPropert === undefined);  // true
```

There is `in` a special operator for this.
```js
"key" in object
```
On the left side of `in` there must be a _property name_. That’s usually a quoted string.
```js
let user = {name: "John", age: 30};

alert( "age" in user );  // true
alert( "bla" in user ); // false
```
If we omit quotes it refers to a variable, that variable should contain the actual name to be tested. For instance:
```js
let user = {age: 30};

let key = "age";
alert( key in user ); // true,  property "age" exists.
```

Checking against `undefined` is also good enough but the `in` operator works even when the object property is storing `undefined`.
```js
let obj = { test: undefined};

alert( obj.test ); // undefined,  but the property exists
alert( "test" in obj); // true
```
___

## `for..in` loop

To walk over all keys of an object.
```js
for (key in object) {
	// for eaach key executes the body
}
```
To output all properties of `user`
```js
let user = {
	name: "John",
	age: 30,
	isAdmin: true,
};

for (let key in user) {
	alert( key );  // to get the name of property
	alert( user[key] );  // to get value of the property
}
```
Note that all “for” constructs allow us to declare the looping variable inside the loop, like `let key` here.

Also, we could use another variable name here instead of `key`. For instance, `"for (let prop in obj)"` is also widely used.


___

### Order in an object

Order of objects when it gets looped depends on whether the property name is "integer" or "non-integer".
for the "integer" even if the number is quoted, it will be converted to number and then ordered according to the number.
for "non-integer" they are listed in the creation order.

To keep a "integer" name to be kept in a creation order is by adding a `+` to the integer like `+41` which makes it a 'non integer'.

```js
let codes = {
	"+49": "Germany",
	"+41": "Switzerland",
	"+44": "Britain",
	"+1": "USA"
	};

for ( let code in codes) {
	alert( +code );
} // 49, 41, 44, 1
```

The `+` operator in `+code` is reconverting them back to integers so `+` wont be visible.