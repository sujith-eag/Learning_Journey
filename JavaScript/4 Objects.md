## Objects

Object is defined when there are multiple values associated with it.
`{}` is used to define an object.
Objects  use names to access its members. `person.name`

```js
let person = {
	name: "eag",
	age: 30
};

person.name = "nea";

person["name"] = "nea";

let selection = 'name';
person[selection] = 'eag';
```
accessing the value  using dot notation
bracket notation,  for taking in input and assigning to an object, not pre-defined

Values of the type `object` are arbitrary collection of properties.
One way of creating is by using `{}` as an expression.
Inside the braces, Each property has a name, colon`:`, and a value.
a list of properties can be written separated by commas.
```js
let dat1 = {
	squirel: false,
	events: ["work", "touched tree", "pizza", "running"]
};

console.log(day1.squirrel);  // false
console.log(day1.wolf);  // undefined

day1.wolf = false;
console.log(day1.wolf);  // false

delete day1.squirrel;
console.log(day1.squirrel);  // undefined
```

Reading a property that doesn't exist gives `undefined`
It is possible to assign value to property expression with the `=` operator.
This creates new property on the object or replaces the old properties value.

Properties whose name are not valid bindings has to be in `""`    `"touch wood": "touched"`
`delete` is an unary operator that removes the named property from an object.

> `{}` braces have two meaning in `js`, 
  At the start of a statement they begin a block of statements. Also describes an object.


#### `Object.keys` to see Properties an object has
```js
console.log(Object.keys( {x:0, y:0, z:2 }));
// ["x", "y", "z"]
```

#### `Object.assign` copies all properties from one object to another
```js
let someA = {a:1, b:2};
Object.assign(someA, {b:3, c:4});
console.log(someA);
// {a:1, b:3, c:4}
```


#### Mutability
The object values can be modified. Properties can be changed causing a single object value to have different content at different times.
> Strings, Numbers, and Boolean's are immutable, cannot be changed in place
```js
let object1 = {value: 10};
object1.value = 15;
```

There is a difference between having two references to the same object and having two different objects that contain the same properties.
```js
let object1 = {value: 10};
let object2 = {value: 10};
let object3 = object1;

console.log( object1 == object2 );  // false
console.log( object1 == object3 ); // true
```

