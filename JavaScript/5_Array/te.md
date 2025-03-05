
Short index of the methods covered:

1. **`indexOf()`** - Searches for an item in an array and returns the index of its first occurrence.
2. **`lastIndexOf()`** - Searches for an item in an array and returns the index of its last occurrence.
3. **`includes()`** - Checks if an item exists in the array, returning `true` or `false`.
4. **`sort()`** - Sorts an array in place. It can be customized using a comparison function for sorting in numerical or lexicographical order.
5. **`shuffle()`** - Randomly shuffles the elements of an array using the Fisher-Yates algorithm.

---

**Arrays** inherit properties from `Array.prototype`, which defines a rich set of array manipulation methods. Most of these methods are **generic**, meaning they work not only for true arrays but for any "array-like object."

## Array Searching and Sorting Methods

Arrays implement `indexOf()`, `lastIndexOf()`, and `includes()` methods that are similar to the same-named methods for strings.

### `indexOf()`, `lastIndexOf()`, `includes()`

These methods are typically used with only one argument: the item to be found.

#### `indexOf()`

```js
arr.indexOf(item, from)
```

- `indexOf` searches through the array for `item`, compares the argument to the array elements using the strict equality (`===`) operator, starting from index `from` to the end, and returns the **index** at which the value was found. If not found, it returns `-1`.

#### `lastIndexOf()`

- `lastIndexOf` searches from the end (right to left).

```js
console.log([1, 2, 3, 2, 1].indexOf(2));    // 1
console.log([1, 2, 3, 2, 1].lastIndexOf(2));  // 3
```

#### `includes()`

```js
arr.includes(item, from)
```

- `includes()` searches through the array for `item`, starting from index `from` to the end, and returns **true** if found. It handles `NaN` properly.

```js
const arr = [NaN];
alert(arr.indexOf(NaN));  // -1
alert(arr.includes(NaN));  // true
```

---

### `sort()` Method

The `sort()` method in JavaScript is used to sort the elements of an array **in place**, meaning it modifies the original array and also returns the sorted array. By default, it converts array elements to strings and sorts them lexicographically (alphabetically or numerically in string order).

#### Basic Usage

```js
let arr = [1, 2, 15];
arr.sort();
alert(arr); // "1, 15, 2"
```

- In this example, `sort()` sorts the numbers as strings. Thus, `1` comes first, followed by `15`, and finally `2`.

#### Sorting with a Custom Comparator

To sort the array numerically or in any specific order, we can pass a **comparison function** to `sort()`. The function should return:

- A **negative number** if `a` should appear before `b`.
- A **positive number** if `a` should appear after `b`.
- **Zero** if `a` and `b` are considered equal.

Sorting numbers in **ascending order**:

```js
let arr = [1, 2, 15];
arr.sort(function(a, b) {
  return a - b;
});
alert(arr);  // [1, 2, 15]
```

#### Shorter Version (Using Arrow Function)

```js
arr.sort((a, b) => a - b);  // Sorts in ascending order
alert(arr); // [1, 2, 15]
```

For **descending order**:

```js
arr.sort((a, b) => b - a);  // Sorts in descending order
alert(arr); // [15, 2, 1]
```

---

### Sorting Strings

When sorting an array of strings, JavaScript compares them lexicographically (alphabetical order):

```js
let arr = ['Banana', 'Apple', 'Orange'];
arr.sort();
alert(arr); // ["Apple", "Banana", "Orange"]
```

To sort strings in **reverse order**, swap `a` and `b` in the comparison function:

```js
arr.sort((a, b) => b.localeCompare(a));
alert(arr); // ["Orange", "Banana", "Apple"]
```

---

### Copying and Sorting an Array

To sort an array while keeping the original array intact, make a copy of the array using `slice()` or the spread operator, and then apply `sort()`:

```js
let arr = ["HTML", "JavaScript", "CSS"];
let sorted = arr.slice().sort();
alert(sorted); // ["CSS", "HTML", "JavaScript"]
alert(arr); // ["HTML", "JavaScript", "CSS"] (original array remains unchanged)
```

Or using the spread operator:

```js
let sorted = [...arr].sort();
```

---

### Sorting Objects by a Property (e.g., Age)

If you have an array of objects and want to sort by a specific property (e.g., `age`), pass a comparison function that compares the property values:

```js
let john = {id: "john", name: "John Smith", age: 25};
let ann = {id: "ann", name: "Ann Smith", age: 29};
let pete = {id: "pete", name: "Pete Peterson", age: 30};

let arr = [john, pete, ann];
arr.sort((a, b) => a.age - b.age);  // Sort by age in ascending order
alert(arr[0].name);  // John Smith
alert(arr[1].name);  // Ann Smith
alert(arr[2].name);  // Pete Peterson
```

To sort in **descending order**, reverse the comparison:

```js
arr.sort((a, b) => b.age - a.age);  // Sort by age in descending order
```

---

### Shuffle an Array

To shuffle an array randomly, use the **Fisher-Yates shuffle algorithm** (more reliable than using `sort()` with `Math.random()`):

```js
function shuffle(array) {
  for (let i = array.length - 1; i > 0; i--) {
    let j = Math.floor(Math.random() * (i + 1)); // Random index between 0 and i
    [array[i], array[j]] = [array[j], array[i]]; // Swap elements
  }
}

let arr = [1, 2, 3];
shuffle(arr);
alert(arr);  // Array shuffled, e.g., [2, 1, 3]
```

---

### Key Points:

- **`sort()`** sorts arrays **in place**, modifying the original array.
- By default, `sort()` converts array elements to strings and sorts lexicographically.
- To **sort numerically**, pass a comparison function to `sort()`.
- **Sort objects by properties** (like age) using a custom comparator.
- **Shuffling** is better done using the **Fisher-Yates shuffle** for randomness rather than relying on `sort()` with `Math.random()`.

---