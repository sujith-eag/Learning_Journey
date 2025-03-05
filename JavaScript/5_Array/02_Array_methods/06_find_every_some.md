
- **`find()`**: Returns the first element in an array that satisfies the provided testing function.
- **`findIndex()`**: Returns the index of the first element that satisfies the provided testing function.
- **`findLastIndex()`**: Returns the index of the last element in an array that satisfies the provided testing function, searching from right to left.
- **`every()`**: Returns `true` if all elements in the array satisfy the provided testing function.
- **`some()`**: Returns `true` if at least one element in the array satisfies the provided testing function.

____

#### find()

The `find()` method returns the **first element** in the array that satisfies the provided testing function.

```js
let foundItem = arr.find(function(item) {
	return condition; // Return true if found
});
```

 - Returns the first element that matches the condition.    
 - If no element is found, it returns `undefined`.

---

#### findIndex()

The `findIndex()` method returns the **index** of the first element in the array that satisfies the provided testing function.

```js
let foundIndex = arr.findIndex(function(item) {
    return condition; // Return true if found
});
```

- Returns the index of the first element that matches the condition.
- If no element is found, it returns `-1`.

---

Both `find()` and `findIndex()` iterate through the array and stop as soon as they find a matching element. If no element matches, `find()` returns `undefined` and `findIndex()` returns `-1`.

```js
let a = [1, 2, 3, 4, 5];

console.log(a.findIndex(x => x === 3)); // 2: value 3 appears at index 2
console.log(a.findIndex(x => x < 0));  // -1: no negative numbers in the array
console.log(a.find(x => x % 5 === 0)); // 5: a multiple of 5
console.log(a.find(x => x % 7 === 0)); // undefined: no multiples of 7 in the array
```

---

In an array of objects, you can use these methods to find an object based on a specific condition.

```js
let users = [
    { id: 1, name: "John" },
    { id: 2, name: "Pete" },
    { id: 3, name: "John" }
];

let user = users.find(item => item.id == 1);
console.log(user.name); // "John"

console.log(users.findIndex(user => user.name == "John")); // 0

console.log(users.findLastIndex(user => user.name == "John")); // 2
```

- **`findLastIndex()`** searches from right to left.

---

### every() and some()

Both `every()` and `some()` methods are predicates that apply a testing function (`fn`) to all elements of the array.

#### every()

The `every()` method tests whether **all** elements in the array pass the provided testing function.

```js
let result = arr.every(function(item) {
    return condition; // Return true if all elements meet the condition
});
```

- Returns `true` if **all** elements satisfy the condition.
- Returns `false` as soon as **one** element does not meet the condition.

#### some()

The `some()` method tests whether **at least one** element in the array passes the provided testing function.

```js
let result = arr.some(function(item) {
    return condition; // Return true if at least one element meets the condition
});
```

- Returns `true` if at least one element satisfies the condition.
- Returns `false` if no element meets the condition.

---

```js
let a = [1, 2, 3, 4, 5];

console.log(a.every(x => x < 10)); // true: all values are < 10
console.log(a.every(x => x % 2 === 0)); // false: not all values are even

console.log(a.some(x => x % 2 === 0)); // true: a has some even numbers
console.log(a.some(isNaN)); // false: a has no non-numbers
```

- **`every()`** is like the mathematical “for all” quantifier (∀). It returns `true` if all elements satisfy the condition.
- **`some()`** is like the mathematical “there exists” quantifier (∃). It returns `true` if there exists at least one element satisfying the condition.


[arr.some(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some) / [arr.every(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) .

---
