
#### Setting and Rerendering

What happens if we keep clicking the Plus button in the calculator? Does the component re-render every time?

Actually, the component won’t re-render. React includes built-in optimization, so `useState` will wait until the end of the current cycle to update the component. It checks whether the value actually changed and then only re-renders the component if it has changed.

Creating a reset counter button

```jsx
import { useState } from 'react';

function Counter()
{
	const [counter, setCounter] = useState(0);
	
	return(
		<main>
			<p>Counter: {counter}</p>
			<button onClick={ ()=> setCounter( (val)=> val+1 )}>
				Increment
			</button>
			
			<button onClick={ ()=> setCounter(0)}> 
				Reset
			</button>
		</main>
	);
}
function App()
{
	return <Counter />;
}
export default App;
```

____

> [!note]
> React Developer Tools with this we’re able to see when any component renders :
> Chrome and Edge: http://mng.bz/wvoq
> Firefox: http://mng.bz/qrYw


#### STATE MUST BE SET TO A NEW VALUE

This condition on the re-render also means that if you set the state value to the same object it already is, even if you changed the object “on the inside,” nothing will happen because there isn’t a re-render.

if you have an array in your state. If you manipulate the array in place and set the same array as the state value again, the component won’t render because nothing has changed from a referential equality perspective, at least.

React doesn’t look inside our state value, but only at the reference.

For this reason, it’s not merely recommended that you don’t mutate state directly, it’s absolutely necessary that you don’t. Doing this correctly requires setting the state value to a new array, which is a duplicate of the old one.

___

```jsx
import { useState } from "react";

function TodoApplication({ initialList }) 
{
	const [todos, setTodos] = useState(initialList);
	
	return (
		<main>
			{todos.map((todo, index) => (
				<p key={todo}>
					{todo}
					<button	onClick={() => {
					setTodos((value) => [
						...value.slice(0, index),
						...value.slice(index+1),
						] );
					}}
					> x </button>
				</p>
			))}
		</main>
	);
}
function App() {
	const items = ["Feed the plants", "Water the dishes", "Clean the cat"];
	return <TodoApplication initialList={items} />;
}
export default App;
```

Sets the state to a new array, which is the concatenation of two things: the old array sliced from the start to just before the deleted element, plus the old array sliced just after the deleted element to the end.

___

#### Using Multiple States

you can have multiple `useState` hooks in the same component, and you often will.

Instead of deleting items, we’ll mark them as completed. Completed items will be rendered in the list with a strike-through. On top of that, we’ll also add a new filter at the top, where you can decide if you want to see all items or only uncompleted items.

ere you can decide if you want to see all items or only uncompleted items. To filter the list, we need to remember whether we should filter out completed items or not. The perfect way to do this is to add another state value that holds this filter flag.

```jsx
import { useState } from "react";

function markDone( list, index)
{
	return list.map(
		(item, i)=> (i===index ? {...item, done: true} : item)
	);
}


function TodoApplication({ initialList }) 
{
	const [todos, setTodos] = useState(initialList);
	const [hideDone, sethideDone] = useState(false);
	
	const filteredTodos = hideDone ? 
			todos.filter(({done}) => !done) : todos;
			
	return (
		<main>
			<div style={ { display: "flex" }}>
				<button onClick={ ()=> sethideDone(false) }
				>Show all </button>

				<button onClick={ ()=> sethideDone(true) }
				>Hide done</button>
			</div>
			{filteredTodos.map( (todo, index)=> (
				<p key={todo.task}>
					{todo.done ? (
						<strike>{todo.task}</strike>
						) : (
						<>
							{todo.task}
							<button onClick={ ()=> setTodos(
								(value)=> markDone(value, todo.index)
								)}
							>x</button>
						</>
						)}
				</p>
				))}
		</main>
	);
}

function App() 
{
	const items = [
		{ task: "Feed the plants", done: false, index: 0 },
		{ task: "Water the dishes", done: false, index: 1},
		{ task: "Clean the cat", done: false, index: 2 },
	];
	
	return <TodoApplication initialList={items} />;
}
export default App;
```

___

#### State Scope

what if we want to have state that spans multiple components? What if we want to access the value in one component, but update it in another?

To do this, we can use properties to pass state values and state setters to the relevant components.

We just had a single component handle everything, we’re now going to introduce a number of components. The `TodoApplication` component is still our stateful component holding the two state values. To aid this one, we add a `FilterButton` and a Task, which take care of rendering the top filter buttons and individual tasks in the list, respectively.

```jsx
import { useState } from "react";

function markDone(list, index) 
{
	return list.map(
		(item, i) => (i === index ? { ...item, done: true } : item)
	);
}

function FilterButton(
	{ current, flag, setFilter, children } ) 
{
	const style = {
		border: "1px solid dimgray",
		background: current === flag ? "dimgray" : "transparent",
		color: current === flag ? "white" : "dimgray",
		padding: "4px 10px",
	};
	return (
		<button
			style={style}
			onClick={() => setFilter(flag)}
			>{children}
		</button>
	);
}

function Task({ task, done, markDone }) 
{
	const paragraphStyle = {
		color: done ? "gray" : "black",
		borderLeft: "2px solid",
	};
	const buttonStyle = {
		border: "none",
		background: "transparent",
		display: "inline",
		color: "inherit",
	};
	
	return (
		<p style={paragraphStyle}>
			<button
				style={buttonStyle}
				onClick={done ? null : markDone}
				>{done ? "✓ " : "◯ "}
			</button>
			{task}
		</p>
	);
}


function TodoApplication({ initialList }) 
{
	const [todos, setTodos] = useState(initialList);
	const [hideDone, setHideDone] = useState(false);
	const filteredTodos = hideDone
		? todos.filter(({ done }) => !done)
		: todos;
		
	return (
		<main>
		<div style={{ display: "flex" }}>
			<FilterButton
				current={hideDone}
				flag={false}
				setFilter={setHideDone}
				>Show all
			</FilterButton>

			<FilterButton
				current={hideDone}
				flag={true}
				setFilter={setHideDone}
				>Hide done
			</FilterButton>
		</div>
		{filteredTodos.map((todo, index) => (
			<Task
				key={todo.task}
				task={todo.task}
				done={todo.done}
				markDone={() => setTodos((value) =>
					markDone(value, todo.index)
					)}
				/>
			))}
		</main>
	);
}

function App() 
{
	const items = [
	{ task: "Feed the plants", done: false, index: 0 },
	{ task: "Water the dishes", done: false, index: 1 },
	{ task: "Clean the cat", done: false, index: 2 },
	];
	return <TodoApplication initialList={items} />;
}

export default App;
```


_____

