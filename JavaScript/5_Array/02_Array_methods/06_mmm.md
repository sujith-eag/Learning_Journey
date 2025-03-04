###  find() findIndex()  findLastIndex()



The `find()` method returns the **first element** in the array that satisfies the provided testing function.

```js
let foundItem = arr.find(function(item) {
    return condition; // Return true if found
});
```

- **Key Points**:
    - Returns the first element that matches the condition.
    - If no element is found, it returns `undefined`.


The `findIndex()` method returns the **index** of the first element in the array that satisfies the provided testing function.

```js
let foundIndex = arr.findIndex(function(item) {
    return condition; // Return true if found
});
```

- **Key Points**:
    - Returns the index of the first element that matches the condition.
    - If no element is found, it returns `-1`.

---

The find() and findIndex() methods are like filter() in that they iterate through
your array looking for elements for which your predicate function returns a truthy
value.

In an array of objects, to find an object with a specific condition.

these methods stop iterating the first time the
predicate finds an element. When that happens, find() returns the matching ele‐
ment, and findIndex() returns the index of the matching element. If no matching
element is found, find() returns undefined and findIndex() returns -1:

```js
let result = arr.find(function(item, index, array) {
// if true is returned, item is returned and iteration is stopped
// for falsy scenario returns undefined
});
```


```js
let a = [1,2,3,4,5];
a.findIndex(x => x === 3)
a.findIndex(x => x < 0)
a.find(x => x % 5 === 0)
a.find(x => x % 7 === 0)
// => 2; the value 3 appears at index 2
// => -1; no negative numbers in the array
// => 5: this is a multiple of 5
// => undefined: no multiples of 7 in the array

```

```js
let users = [
	{id:1, name: "John"},
	{id:2, name: "Pete"},
	{id:3, name: "John"},
];

let user = users.find(item => item.id == 1);

alert(users.name);  // John

alert(users.findIndex(user => user.name == "John"));  // 0

alert(users.findLastIndex(user => user.name == "John"));  // 2
```

`arr.findIndex()` has the same syntax but returns the index where the element was found instead of the element itself.  -1 if noting is found.
`arr.lastIndexOf()` searches from right to left.


__________________

### every() and some()

[arr.some(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some) / [arr.every(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) .
The function `fn` is called on each element of the array similar to `map`. If any/all results are `true`, returns `true`, otherwise `false`.

The every() and some() methods are array predicates: they apply a predicate func‐
tion you specify to the elements of the array, then return true or false.
The every() method is like the mathematical “for all” quantifier ∀: it returns true if
and only if your predicate function returns true for all elements in the array:

These methods behave sort of like `||` and `&&` operators: if `fn` returns a truthy value, `arr.some()` immediately returns `true` and stops iterating over the rest of items; 
if `fn` returns a falsy value, `arr.every()` immediately returns `false` and stops iterating over the rest of items as well.


The `every()` method tests whether all elements in the array pass the provided testing function.

```js
let result = arr.every(function(item) {
    return condition; // Return true if all elements meet condition
});
```

- **Key Points**:
    - Returns `true` if all elements satisfy the condition.
    - Returns `false` as soon as one element does not meet the condition.

---

The `some()` method tests whether **at least one element** in the array passes the provided testing function.

```js
let result = arr.some(function(item) {
    return condition; // Return true if at least one element meets condition
});
```

- **Key Points**:
    - Returns `true` if at least one element satisfies the condition.
    - Returns `false` if no element meets the condition.

---

```js
let a = [1,2,3,4,5];
a.every(x => x < 10)
// => true: all values are < 10.
a.every(x => x % 2 === 0) // => false: not all values are even.
```

The some() method is like the mathematical “there exists” quantifier ∃: it returns
true if there exists at least one element in the array for which the predicate returns
true and returns false if and only if the predicate returns false for all elements of
the array:
```
let a = [1,2,3,4,5];
a.some(x => x%2===0)
a.some(isNaN)
// => true; a has some even numbers.
// => false; a has no non-numbers.
```




____

