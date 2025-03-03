

JavaScript arrays are a special type of object used to store ordered sequences of values.   Unlike regular objects, which use named keys (like strings), arrays use numeric indexes.

An array is an ordered collection of values. Each value
is called an element, and each element has a numeric position in the array, known as its index.

JavaScript arrays may be sparse: the elements need not have contiguous indexes, and there may be gaps. 

JavaScript arrays are a specialized form of JavaScript object, and array indexes are
really little more than property names that happen to be integers.

ES6 introduces a set of new array classes known collectively as “typed arrays.” Unlike
regular JavaScript arrays, typed arrays have a fixed length and a fixed numeric ele‐
ment type.


---

## Creating Arrays

There are several ways to create arrays. The subsections that follow explain how to
create arrays with:
• Array literals
• The ... spread operator on an iterable object
• The Array() constructor
• The Array.of() and Array.from() factory methods


### 1. Array Literals

By far the simplest way to create an array is with an array literal, which is simply a comma-separated list of array elements within square brackets. An array can be initialized with values inside square brackets (`[]`):

```js
let empty = [];
// array with no elements

let primes = [2,3,5,7,11];
// array with 5 neumeric elements

let misc = [1.1, true, "a", ];
// 3 elelemts os different types and 
// a trailing comma
```

If an array literal contains multiple commas in a row, with no value between, the array is sparse. Array elements for which values are omitted do not exist but appear to be undefined if you query them:
```js
let count = [1,,3]; 
// Elements at indexes 0 and 2. No element at index 1

let undefs = [,,]; 
// An array with no elements but a length of 2
```

Array literal syntax allows an optional trailing comma, so `[ , , ] `has a length of 2, not 3.

##### **Arrays of Objects, Arrays, and Functions**

Arrays in JavaScript can contain any type of data, arbitrary expressions, including objects, functions, and even other arrays.

JavaScript arrays are untyped: an array element may be of any type, and different elements of the same array may be of different types. Array elements may even be objects or other arrays, which allows you to create complex data structures, such as arrays of objects and arrays of arrays.

```js
let base = 1024;

let table = [base, base+1, base+2, base+3];
```

**Array of Objects :** storing objects inside an array, which is a common pattern for structured data.
Array literals can contain object literals or other array literals:

```js
let b = [[1, {x: 1, y: 2}], [2, {x: 3, y: 4}]];
```

```js
let journal = [
  {event: ["work", "touched tree", "pizza", "running"], squirrel: false},
  {event: ["work", "ice cream", "lasagna"], squirrel: false},
  {event: ["weekend", "cycling", "peanuts"], squirrel: true}
];
```

**Array of Functions :**
```js
let functionsArray = [
  function() { console.log("Function 1"); },
  function() { console.log("Function 2"); },
  function() { console.log("Function 3"); }
];
```

**Arrays within Arrays :** Arrays can even contain other arrays, creating nested structures:

```js
let arrayOfArrays = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];
```

_____

#### Spread Operator
In ES6 and later, you can use the “spread operator,” ..., to include the elements of one array within an array literal:

```js
let a = [1, 2, 3];
let b = [0, ...a, 4];
// b == [0, 1, 2, 3, 4]
```

The three dots “spread” the array a so that its elements become elements within the
array literal that is being created. It is as if the ...a was replaced by the elements of
the array a, listed literally as part of the enclosing array literal.

The spread operator is a convenient way to create a (shallow) copy of an array:
```js
let original = [1,2,3];
let copy = [...original];
copy[0] = 0; // Modifying the copy does not change the original
original[0]
// => 1
```

The spread operator works on any iterable object. (Iterable objects are what the for/of loop iterates over)
Strings are iterable, so you can use a spread operator to turn any
string into an array of single-character strings:
```
let digits = [..."0123456789ABCDEF"];
digits // => ["0","1","2","3","4","5","6","7","8","9","A","B","C","D","E","F"]
```
Set objects are iterable, so an easy way to remove duplicate elements from an array is to convert the array to a set and then immediately convert the set back to an array using the spread operator:
```
let letters = [..."hello world"];
[...new Set(letters)] // => ["h","e","l","o"," ","w","r","d"]
```


#### **length Property**

The `length` property of an array returns the number of elements in the array. It’s important to note that `length` is **not** zero-based.
When using `[]` the expression between the brackets are evaluated to get the property name.

JavaScript arrays may be sparse: the elements need not have contiguous indexes, and there may be gaps. 
For nonsparse arrays, this property specifies the number of elements in the array. 
For sparse arrays, length is larger than the highest index of any element.


```js
const fruits = ["Banana", "Orange", "Mango"];
console.log(fruits.length);  // 3
```

You can also use `length` to access the last element of an array:

```js
let fruit = fruits[fruits.length - 1];  // "Mango"
```

---





### 2.  'Array()' Constructor


Another way to create an array is with the Array() constructor. You can invoke this
constructor in three distinct ways:
• Call it with no arguments:
let a = new Array();
This method creates an empty array with no elements and is equivalent to the
array literal [].
• Call it with a single numeric argument, which specifies a length:
let a = new Array(10);

This technique creates an array with the specified length. This form of the
Array() constructor can be used to preallocate an array when you know in
advance how many elements will be required. Note that no values are stored in
the array, and the array index properties “0”, “1”, and so on are not even defined
for the array.
• Explicitly specify two or more array elements or a single non-numeric element
for the array:
let a = new Array(5, 4, 3, 2, 1, "testing, testing");
In this form, the constructor arguments become the elements of the new array.
Using an array literal is almost always simpler than this usage of the Array()
constructor.


When the Array() constructor function is invoked with one numeric argument, it
uses that argument as an array length. But when invoked with more than one
numeric argument, it treats those arguments as elements for the array to be created.
This means that the Array() constructor cannot be used to create an array with a sin‐
gle numeric element.

#### Array.of()


In ES6, the Array.of() function addresses this problem: it is a factory method that
creates and returns a new array, using its argument values (regardless of how many of
them there are) as the array elements:
```js
Array.of()  // => []; returns empty array with no arguments

Array.of(10)  // => [10]; can create arrays with a single numeric argument

Array.of(1,2,3)  // => [1, 2, 3]`
```

#### Array.from()

Array.from is another array factory method introduced in ES6. It expects an iterable
or array-like object as its first argument and returns a new array that contains the ele‐
ments of that object. With an iterable argument, Array.from(iterable) works like
the spread operator [...iterable] does. It is also a simple way to make a copy of an
array:
```
let copy = Array.from(original);

let truearray = Array.from(arraylike);
```
Array.from() is also important because it defines a way to make a true-array copy of
an array-like object. Array-like objects are non-array objects that have a numeric
length property and have values stored with properties whose names happen to be
integers. When working with client-side JavaScript, the return values of some web
browser methods are array-like, and it can be easier to work with them if you first
convert them to true arrays:


Array.from() also accepts an optional second argument. If you pass a function as the
second argument, then as the new array is being built, each element from the source
object will be passed to the function you specify, and the return value of the function
will be stored in the array instead of the original value. (This is very much like the
array map() method that will be introduced later in the chapter, but it is more efficient
to perform the mapping while the array is being built than it is to build the array and
then map it to another new array.)


---

### **Associative Arrays in JavaScript**

Although arrays in JavaScript are **indexed by numbers**, you can technically assign a value to a string index.

Arrays with named indexes are called associative arrays or hashes, but
JavaScript **does not support** arrays with named indexes, it always uses Numbered Index.

If named indexes are used, `js` converts array to an object. Then array methods and properties will produce incorrect result.

Example of incorrect usage (for associative arrays):
```js
const person = [];
person["first"] = "John";
person["last"] = "Doe";

console.log(person.length);  // 0 (wrong, since it's an object now)
console.log(person["first"]);  // "John"
console.log(person[0]);  // undefined
```

If you need associative arrays, consider using an **object** instead.


---

#18sep24  Updated on `#03mar25`

___