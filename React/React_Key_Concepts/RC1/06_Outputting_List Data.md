
# Outputting List Data

Typically, in React apps, such list data is received as an array of values.

```js
const products = [
	{id: 'p1', title: 'A Book', price: 59.99},
	{id: 'p2', title: 'A Carpet', price: 129.49},
	{id: 'p3', title: 'Another Book', price: 39.99},
];

function ProductList( {products} ){
	// ... todo
};
```
The goal is to translate this into a list of JSX elements.

Using Basic Java for of loop
```jsx
const productElements = [];

for (const product of products) {
	productElements.push( (
		<li>
			<h2>{product.title}</h2>
			<p>${product.price}</p>
		</li>
	));
}
```

JSX code can be used anywhere where regular JavaScript values (that is, numbers, strings, objects, and so on) can be used. Therefore, you can also push a JSX value onto an array of values. Since it’s JSX code, you can also output content dynamically in those JSX elements.

it is only the first step, since the current data was transformed but still isn’t returned by a component.

JSX actually accepts array values as dynamically outputted values. You can output the productElements array like this:
```jsx
return (
	<ul>
		{productElements}
	</ul>
);
```

>[!important]
>When inserting an array of JSX elements into JSX code, all JSX elements inside that array are outputted next to each other.

Both would be the same
```jsx 
return (
	<div>
		{[<p>Hi there</p>, <p>Another item</p>]}
	</div>
);


return (
	<div>
		<p>Hi there</p>
		<p>Another item</p>
	</div>
);
```

This is one possible approach for outputting list data.



## Mapping List Data

you can replace for loops with an alternative syntax to write less code and improve component readability.

`map()` is a default method that can be called on any JavaScript array. It accepts a function as a parameter and executes that function for every array item. The return value of this function should be the transformed value. `map()` then combines all these returned, transformed values into a new array that is then returned by `map()`.

```jsx
const users = [
	{id: 'u1', name: 'Max', age: 35},
	{id: 'u2', name: 'Anna', age: 32}
];

const userNames = users.map(user => user.name);
// userNames = ['Max', 'Anna']
```

The map() method is often able to produce the same result as that of a for loop but with less code.

```jsx
function ProductsList({products}) {
	const productElements = products.map(product => (
		<li>
			<h2>{product.title}</h2>
			<p>${product.price}</p>
		</li>
		)
	);
	
	return (
		<ul>
			{productElements}
		</ul>
	);
};
```


code can be shortened even more by moving the logic directly into the JSX code:

```jsx
function ProductsList({products}) {
	return (
		<ul>
			{products.map(product => (
				<li>
					<h2>{product.title}</h2>
					<p>${product.price}</p>
				</li>
			)
		)}
	</ul>
	);
};
```

Because it’s very concise, using the map() method (either with the help of an extra variable or constant, or directly inline in the JSX code) is the de facto standard approach for outputting list data in React apps and JSX in general.

## Updating Lists


A new list item is added at some point to a JSX list Or two list items swap places. This can be handled by react if handled in a state-full way.

You must only update the state via the state updating function returned by useState(); otherwise, React will not re-evaluate the component function.

```jsx
// wrong way
import { useState } from 'react';

function Todos() {
	const [todos, setTodos] = useState(['Learn React', 'Recommend this book']);
	
	function handleAddTodo() {
		todo.push('A new todo');
	};
	// ....
```

executing `todos.push('A new todo')` will update the todos array, but React won’t notice it.

```jsx
function handleAddTodo() {
	setTodos(todos.push('A new todo'));
};
```

This is also incorrect because the state updating function should receive the new state as an argument. However, the push() method doesn’t return the updated array. Instead, it mutates the existing array in place.

>[!important]
>when updating an array (or, as a side note, an object in general), you should perform this update in an immutable way (i.e., without changing the original array or object). Instead, a new array or object should be created. This new array can be based on the old array and contain all the old data, as well as any new or updated data.

```jsx
function handleAddTodo() {
	setTodos(curTodos => [...curTodos, 'A new todo']);
};
```

`concat()` can be used instead of spread operator as it returns a new array.
```jsx
function handleAddToDo(){
	setToDos(curTodos => curTodos.concat('A new todo'));
}
```

>[!note]
>A function is passed to the state updating function since the new state depends on the previous state.

When working with state and reference values (that is, objects and arrays), immutability is extremely important to ensure that React is able to pick up changes and no “invisible” (that is, not recognized by React) state changes are performed.

There are different ways of updating objects and arrays immutably, but a popular approach is to create new objects or arrays and then use the spread operator (...) to merge existing data into those new arrays or objects.

___

### Problem with List Items

The code of previous section will throw a key uniqueness error in the developers tools. Where React will complain about missing keys.

For every new to-do item that is added to the list. React will destroy the existing DOM nodes (that is, the existing `<li>` items), just to then recreate them immediately. The items existed before, and their content (the to-do text) didn’t change.

This happens because React has no way of knowing that only one DOM node should be inserted. It cannot tell that all other DOM nodes should stay untouched because React only received a brand-new state value: a new array, filled with new JavaScript objects. I cannot know only one item changed.

>[!note]
>That’s why React uses the concept of keys when working with list data and rendering list items. Keys are simply unique identifier values that can (and should) be attached to JSX elements when rendering list data. Keys help React identify elements that were rendered before and didn’t change.
>

By allowing the unique identification of all list elements, keys also help React to move (list item) DOM elements around efficiently.

Keys are added to JSX elements via the special built-in key prop that is accepted by every component:
```jsx
<li key={todo.id}>{todo.text}</li>
```

The key prop requires a value that is unique for every list item. No two list items should have the same key. In addition, good keys are directly attached to the underlying data that makes up the list item.

>[!note]
>List item indexes are poor keys because the index isn’t attached to the list item data. If you reorder items in a list, the index isn't reordered so stay the same. 

Good keys are unique id values, such that every id belongs to exactly one value. If that value moves or is removed, its id should move or disappear with that value.

Sometimes, even the values themselves can be used as keys.

```jsx
const hobbies = ['Sports', 'Cooking'];

hobbies.map(hobby => <li key={hobby}>{hobby}</li>);
```
you typically won’t have duplicate values as it doesn’t make sense for a hobby to be listed more than once in an array like this. Therefore, the values themselves qualify as good keys:

With keys added to list item elements, React is able to identify all items correctly. When the component state changes, it can identify JSX elements that were rendered before already. Those elements are therefore not destroyed or recreated anymore.


____

### Summary and Key Takeaways
* Like any other JavaScript value, JSX elements can be set and changed dynamically, based on different conditions.
* Content can be set conditionally via if statements, ternary expressions, the logical “and” operator (&&), or in any other way that works in JavaScript.
* There are multiple ways to handle conditional content—any approach that would work in vanilla JavaScript can also be used in React apps.
* Arrays with JSX elements can be inserted into JSX code and will lead to the array elements being outputted as sibling DOM elements.
* List data can be converted into JSX element arrays via for loops, the map() method, or any other JavaScript approach that leads to a similar conversion.
* Using the map() method is the most common way of converting list data to JSX element lists.
* Keys (via the key prop) should be added to the list JSX elements to help React update the DOM efficiently.

_____

