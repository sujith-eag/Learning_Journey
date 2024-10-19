
Primitive data type can contain only a single thing, Objects data types are used to store a collection of data.

## Objects
Objects a collection of key-value pairs. `{}` is used to define an object.
key is a string, value can be anything.

>`{}` braces have two meaning in `js`, 
  At the start of a statement they begin a block of statements. Also describes an object.

An empty object can be created in two ways
```js
let user = new Object();   // "object constructor" syntax

let user = {}  // "object literal syntsx" syntx
```
Usually, the figure brackets `{...}` are used. That declaration is called an _object literal_.

_______________


When a primitive variable is defined, it will contain a copy of the information provided to it.
When an object is defined it contains a reference to the object provided to it. So many variables point to same object with reference.
```js
const obj = {data: 42};
const objCopy = obj;

objCopy.data = 43;

console.log(obj);  // data: 43
console.log(objCopy); // data: 43
```
This is how the DOM object gets edited using storing its references in `js` variables.
```js
const element = document.querySelector("#container");
element.style.backgroundColor = 'red';
```



## Literals and properties

Values of the type `object` are arbitrary collection of properties.
Inside the braces`{}`, Each `property` has a `key`or `name` before the colon`:`
and a `value` to the right of it.
List of properties can be written separated by commas.
```js
let user = {
	name: "John",
	age: 30,
	"likes birds": true,
};
alert(user.name);  // john
user.isAdmin = true;  // assigning a boolean
delete user.age;  // deletes that property
```

There is no restriction on names of object properties
They can be any string or number, symbol even reserved words.

Properties whose name are not valid bindings and multi word has to be in `""`quotes.
`"touch wood": "touched"` 


### Object Literal

```js
const person = {
  name: ["Bob", "Smith"],
  
  age: 32,
  
  bio: function () {
    console.log(`${this.name[0]} ${this.name[1]} is ${this.age} years old.`);
  },
  
  introduceSelf: function () {
    console.log(`Hi! I'm ${this.name[0]}.`);
  },
};

// person.bio();
	// Bob smith is 32 years old.
```

An object like this is called an object literal - we have written out the object contents as we've come to create it.

It is common to create an object using an object literal when you want to transfer a series of structured, related data items in some manner, (sending a request to the server to be put into a database).
Sending a single object is efficient than sending several items.
It is easier to work with an array wen you want to identify individual items by name.

When the member objects are functions, there is a simpler syntax.
```js
bio: function () {...},
introduceSelf: function() {...},
// simpler is omitting the function
bio() {...},
introduceSelf() {...},
```

### Dot Notation

The object name acts as the namespace - entered first to access anything inside the object. Next is a dot `.` , then what needs to be accessed.
```js
person.age;
person.bio()
```
Property values are accessing using dot notation.

An object can itself be an Objects property.
That is, objects can contain objects. 
```js
const person = {
	name: {
		first: "Bob",
		last: "Smith"
		},
};

// to access this extra chaining is needed.
person.name.first;

// using bracket notation
person["name"]["first"];
```

________

### Square Bracket notation 

This is similar to how items are accessed in an array.
Instead of index numbers to select an item, name associated with each member's value is used.

So objects are also called as ***associative arrays***

Dot notation is preferred as it is more easy to read but,
if an object property name is held in a variable, then dot notation cannot be used to access the value.

```js
const person = {
  name: ["Bob", "Smith"],
  age: 32,
};

function logProperty(propertyName) {
  console.log(person[propertyName]);
}

logProperty("name");   // ["Bob", "Smith"]
logProperty("age");   // 32
```

For multi word properties, the dot access doesn't work
`user.likes birds = true`
Square bracket notation works with any string.
```js
let user = {};

user["likes birds"] = true  // setting
alert(user["likes birds"]);  // true
delete user["likes birds"];  // delete
```
square brackets allow a way to obtain the property name as the result of any expression.
```js
let key = "likes birds";  // assign value to variable
user[key] = true;
// same as user["likes birds"] = true;
```

```js
let user = {
	name: "John",
	age: 30
};

let key = prompt("What do you know about user?", "name");
// access by variable
alert( user[key] );  // John ???
```

_________
# for..in loop
[[4_for...in_loop|Details here]]
______________

# Property Value Shorthand

In real code we often use existing variables as values for property names.
```js
function makeUser(name, age) {
	return {
		name: name,
		// can be written as just
		name,
		age, 
		age: age,
		// ...other properties
	};
}

let user = makeUser("John", 30); 
alert(user.name);  // John`
```

```js
let user = {
	name,  // same as name:name
	age: 30,
}
```





___

## Summary

Objects are associative arrays with several special features.

They store properties (key-value pairs), where:
- Property keys must be strings or symbols (usually strings).
- Values can be of any type.

To access a property, we can use:
- The dot notation: `obj.property`.
- Square brackets notation `obj["property"]`. Square brackets allow taking the key from a variable, like `obj[varWithKey]`.

Additional operators:
- To delete a property: `delete obj.prop`.
- To check if a property with the given key exists: `"key" in obj`.
- To iterate over an object: `for (let key in obj)` loop.

What we’ve studied in this chapter is called a “plain object”, or just `Object`.

