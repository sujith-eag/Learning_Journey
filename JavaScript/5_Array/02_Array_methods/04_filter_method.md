

The `filter()` method similar to `map()` but it creates a **new array** containing only the elements from the original array that satisfy a given condition. The condition is specified by a **callback function** passed to `filter()`, which should return a boolean value (`true` or `false`) for the element to get stored.

`filter()` does **not modify** the original array; it is a **pure function**.

---

```js
let newArray = arr.filter(function(item, index, array) {
    return condition; // Return true/false
});
```

- **`item`**: The current element being processed.
- **`index`**: The index of the current element.
- **`array`**: The array `filter()` was called on.

---

**Filter Values**
```js
let a = [5, 4, 3, 2, 1];
a.filter(x => x < 3)
// => [2, 1]; values less than 3

a.filter((x, i) => i % 2 === 0) 
// => [5, 3, 1]; every other value
```

`filter()` skips missing elements in sparse arrays, and the return value is always dense. You can close the gaps in a sparse array like this:

```js
let dense = sparse.filter(() => true);
```

To remove `undefined` and `null` elements, you can use `filter()` like this:

```js
a = a.filter(x => x !== undefined && x !== null);
```

---

#### Example 1: Filter Strings that Start with "L"

```js
const cats = ["Lepord", "Jaguar", "Tiger", "Lion"];

function lCat(cat) {
    return cat.startsWith("L");
}

const newList = cats.filter(lCat);

console.log(newList);  // ["Lepord", "Lion"]
```

---

#### Example 2: Filter Out Odd Numbers

```js
const arr = [1, 2, 3, 4, 5];

function isOdd(num) {
    return num % 2 !== 0;
}

const oddNums = arr.filter(isOdd);

console.log(oddNums);  // [1, 3, 5]
```

---

#### Example 3: Filter with a Callback Directly

```js
let users = [
    { id: 1, name: "John" },
    { id: 2, name: "Pete" },
    { id: 3, name: "John" }
];

let someUser = users.filter(item => item.id < 3);

console.log(someUser.length);  // 2
```

---

#### Example 4: Filter Using an Object Method

You can also use a method from an object to filter an array:

```js
let army = {
    minAge: 18,
    maxAge: 27,

    canJoin(user) {
        return user.age >= this.minAge && user.age < this.maxAge;
    }
};

let users = [{ age: 16 }, { age: 20 }, { age: 23 }, { age: 30 }];

let soldiers = users.filter(user => army.canJoin(user));

alert(soldiers.length);  // 2
alert(soldiers[0].age);  // 20
alert(soldiers[1].age);  // 23
```

You can also use `filter()` with a method like this:

```js
let soldiers = users.filter(army.canJoin, army);
```

---

#### Example 5: Filter Values in a Specified Range

You can filter values within a specific range using `filter()`:

```js
function filterRange(arr, a, b) {
    return arr.filter(item => item >= a && item <= b);
}

let arr = [5, 3, 8, 1];
let filtered = filterRange(arr, 1, 4);

console.log(filtered);  // [3, 1]
```

---

