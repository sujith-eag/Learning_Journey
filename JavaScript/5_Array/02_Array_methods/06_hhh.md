

[arr.flat(depth)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)/[arr.flatMap(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap) create a new flat array from a multidimensional array.

### flat(depth)

Creates a new flat array from a multidimensional array.
The flat method creates a new array with sub-array elements concatenated to a specified depth.

In ES2019, the flat() method creates and returns a new array that contains the same
elements as the array it is called on, except that any elements that are themselves
arrays are “flattened” into the returned array :

```js
const myArray = [ [1,2], [3,4], [5,6] ];

const newArray = myArray.flat();
// 1,2,3,4,5,6
```


```
[1, [2, 3]].flat()
[1, [2, [3]]].flat()
// => [1, 2, 3]
// => [1, 2, [3]]
```

Elements of the
original array that are themselves arrays are flattened, but array elements of those
arrays are not flattened. If you want to flatten more levels, pass a number to flat():
```js
let a = [1, [2, [3, [4]]]];
a.flat(1) // => [1, 2, [3, [4]]]
a.flat(2)
// => [1, 2, 3, [4]]
a.flat(3)
// => [1, 2, 3, 4]
a.flat(4)
// => [1, 2, 3, 4]
```

### flatMap(fn)

it first maps all elements of an array and then creates a new array by flattening the array.

```js
const myArray = [1,2,3,4,5,6];

const newArray = myArray.flatMap( x => [x, x*10] );
// [1, 10, 2, 20, 3, 30, 4, 40, 5, 50, 6, 60]
```

The flatMap() method works just like the map() method 
except that the returned array is automatically flattened as if passed to flat(). That
is, calling a.flatMap(f) is the same as (but more efficient than) a.map(f).flat():
```
let phrases = ["hello world", "the definitive guide"];
let words = phrases.flatMap(phrase => phrase.split(" "));
words // => ["hello", "world", "the", "definitive", "guide"];
```
You can think of flatMap() as a generalization of map() that allows each element of
the input array to map to any number of elements of the output array. In particular,
flatMap() allows you to map input elements to an empty array, which flattens to
nothing in the output array:
```
// Map non-negative numbers to their square roots
[-2, -1, 1, 2].flatMap(x => x < 0 ? [] : Math.sqrt(x)) // => [1, 2**0.5]
```

____


### concat()

The concat() method creates and returns a new array that contains the elements of
the original array on which concat() was invoked, followed by each of the arguments
to concat().

f any of these arguments is itself an array, then it is the array elements
that are concatenated, not the array itself.

`arr.concat` creates a new array that includes values from other arrays and additional items.
```js
arr.cocat(arg1, arg2...)
```
accepts any number of arguments - either arrays or values.

Used to create a new array by merging (concatenating) existing arrays and returns a new array without changing the old ones.

```js
let a = [1,2,3];
a.concat(4, 5)
a.concat([4,5],[6,7])
a.concat(4, [5,[6,7]])
a
// => [1,2,3,4,5]
// => [1,2,3,4,5,6,7]; arrays are flattened
// => [1,2,3,4,5,[6,7]]; but not nested arrays
// => [1,2,3]; the original array is unmodified
```

```js
const myGirls = ["Cel", "Lon"];
const myBoys = ["Em", "Lin"];
const myPets = ["cat", 'Dog'];

const myChildren = myGirls.concat(myBoys);
const family = myGirls.concat(myBoys, myPets);

const myKids = myGirls.concat("daisy");
```
It can take strings also as arguments.
Normally, it only copies elements from arrays. Other objects, even if they look like arrays, are added as a whole.

Note that concat() makes a new copy of the array it is called on. In many cases, this
is the right thing to do, but it is an expensive operation. If you find yourself writing
code like a = a.concat(x), then you should think about modifying your array in
place with push() or splice() instead of creating a new one.

