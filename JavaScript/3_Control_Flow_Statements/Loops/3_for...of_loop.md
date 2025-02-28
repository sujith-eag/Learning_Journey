
The `for/of` loop is a convenient and simpler way for iterating over **iterable objects** (e.g., arrays, strings, maps, sets).
ES6 defines a new loop statement: `for/of`. This new kind of loop uses the for keyword but is a completely different kind of loop than the regular `for` loop. (It is also completely different than the older `for/in` loop)


```js
for (const element of iterable) {
    // code to run for each element
}
```

The loop body runs once for each element of the data array.
Before each execution of the loop body, the next element of the array is assigned to the element variable. Array elements are iterated in order from first to last.

```js
let data = [1, 2, 3, 4, 5, 6, 7, 8, 9], sum = 0;

for(let element of data) {
	sum += element;
}
sum
// => 45
```

Arrays are iterated “live”—changes made during the iteration may affect the outcome
of the iteration. If we modify the preceding code by adding the line data.push(sum);
inside the loop body, then we create an infinite loop because the iteration can never
reach the last element of the array.

[for…of](https://javascript.info/array#loops) and [iterables](https://javascript.info/iterable) for looping over arrays and iterable objects.
[[6_Iterables|Iterable]]

___

### 'for/of' with Array

```js
for (let i = 0; i < cats.length; i++) {
    console.log(cats[i]);
}
// Output: Lepord, Jaguar, Tiger, Lion
```
This is the traditional `for` loop, which uses an index to access array elements.

```js
const cats = ["Lepord", "Jaguar", "Tiger", "Lion"];

for (const cat of cats) {
    console.log(cat);
}
// Output: Lepord, Jaguar, Tiger, Lion
```

___

### 'for/of' with objects

Objects are not (by default) iterable. Attempting to use for/of on a regular object
throws a TypeError at runtime:
```js
let o = { x: 1, y: 2, z: 3 };

for(let element of o) { 
	console.log(element);
}
// Throws TypeError because o is not iterable
```

`for/in` is used to iterate through properties of an object directly, or use the `for/of` loop with `Object.keys()` method. This works because `Object.keys()` returns an array of property names for an object,
and arrays are iterable with `for/of`. 

```js
let o = { x: 1, y: 2, z: 3 };
let keys = "";

for(let element of Object.keys(o)) { 
	keys += k;
}
keys     // "xyz"
```

Similarly using `Object.values()`
```js
let sum = 0;

for(let v of Object.values(o)) {
	sum += v;
}
sum // => 6
```

And if you are interested in both the keys and the values of an object’s properties, you
can use for/of with Object.entries() and destructuring assignment:
```js
let pairs = "";

for(let [k, v] of Object.entries(o)) {
	pairs += k + v;
}
pairs // => "x1y2z3"
```
`Object.entries()` returns an array of arrays, where each inner array represents a
key/value pair for one property of the object.


---

### 'for/of' with string

Strings are iterable character-by-character in ES6

```js
let word = "Hello";

for (const char of word) {
    console.log(char);
}
// H  // e  // l  // l  // o
```

```js
let frequency = {};
for(let letter of "mississippi") {
	if (frequency[letter]) {
		frequency[letter]++;
	} else {
		frequency[letter] = 1;
	}
}
frequency
// => {m: 1, i: 4, s: 4, p: 2}
```


___

### 'for/of' with Set and Map


The built-in ES6 Set and Map classes are iterable. When you iterate a Set with `for/of`, the loop body runs once for each element of the set.

- **Sets**:
```js
const set = new Set([1, 2, 3, 4, 5]);

for (const number of set) {
    console.log(number);
}
// 1  // 2  // 3  // 4  // 5
```

print the unique words in a string of text:
```js
let text = "Na na na na na na na na Batman!";
let wordSet = new Set(text.split(" "));
let unique = [];

for(let word of wordSet) {
	unique.push(word);
}
unique 
// => ["Na", "na", "Batman!"]
```

* Map

Maps are an interesting case because the iterator for a Map object does not iterate the
Map keys, or the Map values, but key/value pairs. Each time through the iteration, the
iterator returns an array whose first element is a key and whose second element is the
corresponding value. Given a Map m, you could iterate and destructure its key/value.

```js
let m = new Map([[1, "one"]]);

for(let [key, value] of m) {
	key      // => 1
	value    // => "one"
}
```


```js
const map = new Map([
    ['key1', 'value1'],
    ['key2', 'value2']
]);

for (const [key, value] of map) {
    console.log(`${key}: ${value}`);
}
// key1: value1   // key2: value2
```




---

### **Create a Function 'unique(arr)'**

Function that returns an array of unique items from the input array:

```js
function unique(arr) {
    let result = [];

    for (let str of arr) {
        if (!result.includes(str)) {
            result.push(str);
        }
    }
    return result;
}

let strings = ['hare', 'krisna', 'hare', 'krishna', 'krishna', 'krishna', 'hare', 'hare', ':-0'];

alert(unique(strings)); // Output: hare, krisna, krishna, :-0
```

This function iterates through the `arr` using `for...of` and checks if each element is already in the `result` array using the `includes()` method. If the element is not present, it's added to the `result`.

**Note:** This approach has repeated comparisons (`includes()`), which is inefficient for large arrays because `includes()` has a time complexity of O(n). A more optimized solution might involve using a `Set` (which guarantees uniqueness and has O(1) lookup time) or leveraging other data structures.

---

### Optimized Version Using 'Set'

Instead of using an array and `includes()`, you can use a `Set`, which automatically handles uniqueness for you:

```js
function unique(arr) {
    return [...new Set(arr)];
}

let strings = ['hare', 'krisna', 'hare', 'krishna', 'krishna', 'krishna', 'hare', 'hare', ':-0'];

alert(unique(strings)); 
// Output: hare, krisna, krishna, :-0
```

This version is much more efficient because the `Set` data structure automatically removes duplicates.

---

