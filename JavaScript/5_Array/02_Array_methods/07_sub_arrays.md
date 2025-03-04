
## Extracting parts of array

methods for extracting, replacing,
filling, and copying slices.

### slice()

The slice() method returns a slice, or subarray, of the specified array. Its two argu‐
ments specify the start and end of the slice to be returned.

```js
arr.slice([start], [end])
```

`slice` returns a new array copying to it all the elements from `start` to `end` (not including `end` but up to end). 
Doesn't remove any element from original. makes a sub array.
Both start and end can be negative, in that case position from the array end is assumed.

If only one argu‐
ment is specified, the returned array contains all elements from the start position to
the end of the array.
When end index is not given, all elements after the start index is taken.
```js
const fruits = ["Bannana", "Orange", "Lemon", "Apple", "Mango"]

// copy from index 1 upto index 3, i.e 1,2
const citrus = fruits.slice(1,3);   // [Orange, Lemon]

// copy from index 2 till the end, including end
const citrus = fruits.slice(2);  //  [Lemon, apple, mango]

// copy from index 2 upto 4,  2,3
console.log([0, 1, 2, 3, 4].slice(2, 4));   // [2, 3]

// copy from index 2 till end
console.log([0, 1, 2, 3, 4].slice(2));  // [2, 3, 4]


let arr = [ "t", "e", "s", "t"]
// copy from -2 till end
aler( arr.slice(-2) );   // s, t

alert( arr.slice(1, 3) );  // e, s
```


______________




### copyWithin()

[arr.copyWithin(target, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin) – copies its elements from position `start` till position `end` into _itself_, at position `target` (overwrites existing).
```js
arr.copyWithin(target, start, end)
```

Copies array elements to another position in an array by overwriting the existing value.

copies its elements from position `start` till position `end` into itself, at position `target` (overwrites existing).

It cannot add items to an array so does not change the length of the array.
```js
const fruits = ["Bannana", "Orange", "Mango", "Kiwi"];

fruits.copyWithin(2,0);  // copy to index[2], all elements from [0]
// Bannana, Orange, Bannana, Orange

fruits.copyWithin(2,0,2); //copy to index 2, the elements from 0 to 2
```

```
let a = [1,2,3,4,5];
a.copyWithin(1)
// => [1,1,2,3,4]: copy array elements up one
a.copyWithin(2, 3, 5) // => [1,1,3,4,4]: copy last 2 elements to index 2
a.copyWithin(0, -2)
// => [4,4,3,4,4]: negative offsets work, too
```

copyWithin() copies a slice of an array to a new position within the array. It modifies
the array in place and returns the modified array, but it will not change the length of
the array. The first argument specifies the destination index to which the first element
will be copied. The second argument specifies the index of the first element to be
copied. If this second argument is omitted, 0 is used. The third argument specifies the
end of the slice of elements to be copied. If omitted, the length of the array is used.
Elements from the start index up to, but not including, the end index will be copied.
You can specify indexes relative to the end of the array by passing negative numbers,
just as you can for slice():


_______________

#### fill()

[arr.fill(value, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill) – fills the array with repeating `value` from index `start` to `end`.

[manual](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

The fill() method sets the elements of an array, or a slice of an array, to a specified
value. It mutates the array it is called on, and also returns the modified array:
```
let a = new Array(5);
a.fill(0)
a.fill(9, 1)
a.fill(8, 2, -1)
// Start with no elements and length 5
// => [0,0,0,0,0]; fill the array with zeros
// => [0,9,9,9,9]; fill with 9 starting at index 1
// => [0,9,8,8,9]; fill with 8 at indexes 2, 3
```

The first argument to fill() is the value to set array elements to. The optional sec‐
ond argument specifies the starting index. If omitted, filling starts at index 0. The
optional third argument specifies the ending index—array elements up to, but not
including, this index will be filled. If this argument is omitted, then the array is filled
from the start index to the end. You can specify indexes relative to the end of the
array by passing negative numbers, just as you can for slice().



