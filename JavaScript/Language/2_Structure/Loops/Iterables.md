https://javascript.info/iterable

## Symbol.iterator
.
.
.
Objects that can be used in `for..of` are called _iterable_.

- Technically, iterables must implement the method named `Symbol.iterator`.
    - The result of `obj[Symbol.iterator]()` is called an _iterator_. It handles further iteration process.
    - An iterator must have the method named `next()` that returns an object `{done: Boolean, value: any}`, here `done:true` denotes the end of the iteration process, otherwise the `value` is the next value.
- The `Symbol.iterator` method is called automatically by `for..of`, but we also can do it directly.
- Built-in iterables like strings or arrays, also implement `Symbol.iterator`.
- String iterator knows about surrogate pairs.

## String is iterable
for a string `for...of` loops over its characters.

```js
for (let char of "test") {
	alert( char ); // t, e, s, t
}
```
strings are both iterable (`for..of` works on them) and array-like (they have numeric indexes and `length`).

Objects that have indexed properties and `length` are called _array-like_. Such objects may also have other properties and methods, but lack the built-in methods of arrays.

## Array.from

There’s a universal method [Array.from](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) that takes an iterable or array-like value and makes a “real” `Array` from it. Then we can call array methods on it.

```js
let arrayLike = {
	0: "Hello",
	1: "World",
	length: 2
	};

let arr = Array.from(arrayLike);

alert(arr.pop());  // World

```
`Array.from` takes the object, examines it for being an iterable or array-like, then makes a new array and copies all items to it.

```js
Array.from(obj [, mapFn, thisArg])
```
The optional second argument `mapFn` can be a function that will be applied to each element before adding it to the array, and `thisArg` allows us to set `this` for it.
So it provides a optional "mapping" function.


