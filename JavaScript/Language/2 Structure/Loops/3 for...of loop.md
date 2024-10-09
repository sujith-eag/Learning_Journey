
###  `for...of` loop

[for…of](https://javascript.info/array#loops) and [iterables](https://javascript.info/iterable) for looping over arrays and iterable objects.

A basic tool to loop through a collection like an array.
```js
const cats = ["Lepord", "jaguar", "Tiger"];

for (const cat of cats) {
	console.log(cat);
}
```
[[Iterables|Iterable]] objects are a generalization of arrays. That’s a concept that allows us to make any object useable in a `for..of` loop.

There are many other built-in objects, that are iterable as well. 
Strings are also iterable. If an object isn’t technically an array, but represents a collection (list, set) of something, then `for..of` is a great syntax to loop over it.

____________

Create a function `unique(arr)` that should return an array with unique items of `arr`.
```js
function unique(arr) {
	let result = [];

	for( let str of arr) {
		if(!result.includes(str)) {
			result.push(str);
		}
	}
	return result;
}

let strings = ['hare', 'krisna', 'hare', 'krishna', 'krishna', 'krishna', 'hare', 'hare', ':-0']

alert( unique(strings) ); // hare, krishna, :-0 
```
Lot of repeated comparisons, not optimized.


______________



