

The `map()` method is used to transform an array by applying a provided/callback function to each of its elements. It returns a **new array** containing the results/returns of calling the provided function on every element of the original array, without modifying the original array itself.

```js
let result = arr.map(function(item, index, array) {
    // returns the transformed value instead of item
});
```

- **`item`**: The current element being processed.
- **`index`**: The index of the current element.
- **`array`**: The array `map()` was called on.

```js
let a = [1, 2, 3];
let squared = a.map(x => x * x);

console.log(squared);
// => [1, 4, 9]  // Each element is squared
```

The `map()` method expects a `callback` function as an argument. The callback function is invoked for each element in the array, and it should return a value. The `map()` method then collects and returns a new array with the transformed values.


____

#### Example 1: Add 1 to Each Number in an Array

The `map()` method is commonly used to transform an array by applying a function to each element, like adding `1` to each element of an array:

```js
const arr = [1, 2, 3, 4, 5];

function addOne(num) {
    return num + 1;
}

const mappedArr = arr.map(addOne);

console.log(mappedArr);  // [2, 3, 4, 5, 6]
```

Alternatively, you can use an **inline arrow function**:

```js
const mappedArr = arr.map(num => num + 1);
```

This creates a new array where each value is incremented by `1`, while the original array remains unchanged.

---

#### Example 2: Map to Lengths of Strings

You can also use `map()` to derive new data from an existing array. 

**To create an array of string lengths:**
```js
let names = ["Bilbo", "Gandalf", "Nazgul"];
let lengths = names.map(item => item.length);

console.log(lengths);  // [5, 7, 6]
```

Here, `map()` iterates over the `names` array and returns the length of each string.

---

#### Example 3: Transforming Strings to Uppercase

The `map()` function can be used to modify strings. For example, converting all the cat names to uppercase:

```js
const cats = ["Leopard", "Jaguar", "Tiger", "Lion"];

function toUpper(string) {
    return string.toUpperCase();
}

const upperCats = cats.map(toUpper);

console.log(upperCats);  // ["LEOPARD", "JAGUAR", "TIGER", "LION"]
```

In this case, the `toUpper()` function is applied to each string in the `cats` array, returning a new array where all strings are capitalized.

---

#### Example 4: Map to Names

You can use `map()` to extract specific properties from objects in an array. For example, if you have an array of user objects and want to get an array of just the names:

```js
let john = { name: "John", age: 25};
let pete = { name: "Pete", age: 30};
let mary = { name: "Mary", age: 28};

let users = [john, pete, mary];

let names = users.map(user => user.name);

console.log(names);  // ["John", "Pete", "Mary"]
```

---

#### Example 5: Map to Objects with New Properties

If you need to transform an array of objects into a new array with different properties, `map()` is useful. For example, combining a user's `name` and `surname` into a `fullName`:

```js
let john = { name: "John", surname: "Smith", id: 1};
let pete = { name: "Pete", surname: "Hunt", id: 2};
let mary = { name: "Mary", surname: "Key", id: 3};

let users = [john, pete, mary];

let usersMapped = users.map(user => ({
    fullName: `${user.name} ${user.surname}`,
    id: user.id
}));

console.log(usersMapped);
// [
//   { fullName: "John Smith", id: 1 },
//   { fullName: "Pete Hunt", id: 2 },
//   { fullName: "Mary Key", id: 3 }
// ]
```

Note: In the above code, we use arrow functions with parentheses `({})` to return an object from the callback function. Without the parentheses, JavaScript treats `{` as the start of a function body instead of an object literal.

---

#### Example 6: Convert Kebab-case to CamelCase

You can use `map()` to apply transformations to strings, such as converting from `kebab-case` to `camelCase`:

```js
function camelCase(str) {
    return str.split('-')
        .map((word, index) => index === 0 ? word : word[0].toUpperCase() + word.slice(1))
        .join('');
}

console.log(camelCase("background-color"));  // "backgroundColor"
console.log(camelCase("list-style-type"));   // "listStyleType"
```

- **`split('-')`**: Splits the string into an array of words based on the `-` delimiter.
- **`map()`**: Capitalizes the first letter of each word (except the first one), while keeping the rest of the word in lowercase.
- **`join('')`**: Joins the words back together to form a single string in camelCase.

---
