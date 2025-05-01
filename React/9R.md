### Making React Interactive with States


The output of the components we’ve created so far depends on nothing but their properties. In other words, the components are “pure” in functional programming terms. The components have no other inputs and no side effects. If you give the same component the same properties, you’ll always get the same result and nothing but that result.

Components that depend only on their properties and have no internal logic beyond that are also called stateless components.

If we want to update something when a button is clicked or an input is filled, we need to store that somewhere and pass that information to some other component to react to it.

___

state refers to the ability to change over time by using internal variables. The same component can have one internal state that results in one Java-Script XML (JSX) output at one point, and later have a different state that results in a different output.

Whether it’s clicked or not is the state of the button, and a component that holds state is stateful.

___

State is essential for making any kind of interactive application. If your application
doesn’t have any state, it means that your application is completely static—it can’t
change at all once opened in the browser. This might be fine for a blog post or a rec-
ipe, but if you want users to log in, update, click, or in any other way interact with your
application to influence what is being shown, you need your application to be stateful.

React components are individually stateful. Keeping state in a component is what makes your React application as a whole stateful.

___

### React component state

* Stateful component—A stateful component is independent of its context and has the ability to update itself based on internal triggers.
* Stateless component—A stateless component can only change or update when its parent component provides it with new properties.

A clock component that can display some time of day based on a property passed to it by its parent, versus a clock component that is able to update itself every second and continually display the current time.

___

Any state used in a web application belongs to one of three categories:
* Application data
* UI state
* Form data

#### Application Data

Application data is the data the user is working on, updating, or reading. If you’re
building a web application where users can log in, the information about the user is
application data.

Application data is most often stored on a global level in your application. 

#### UI State

UI state refers to the current state of UI components, such as which tab is currently active, whether a panel is collapsed or not, whether the menu is open or not, and so on.

UI state values are most often kept as local as possible.

#### Form Data

While the user is interacting with a form, entering data, moving from one form
field to the next, the current state of the form is often kept in local state in the compo-
nent that covers all the form fields.

___

What not to store in state
* Values that don't change - configuration values
* copies of other state values
* Duplicates of the same data

___

### Adding State to a functional component

Creating a click counter. We need a way to initialize our counter, display the current value, and increment the counter every time we click a button. We need to let React know that a value has been updated, which means we need to go through the React-specific API.

To do this in a functional component, we need to use a function from the React package named useState. It takes an initial value and returns the current state and an update function.

```jsx
import { useState } from 'react';

function Counter()
{
	const [ counter, setCounter ] = useState(0);
	
	return(
		<main>
			<p>Clicks : {counter}</p>
			<button 
				onClick={() => setCounter( (value) => value+1 )}>
				Increment </button>
		</main>
	);
}

function App()
{
	return <Counter />;
}
export default App;
```

* Import the function `useState` from the React package. (it is a hook)
* Call `useState` in the functional component and supply an initial value.
* Destructure the response from calling useState as two array elements:
	– The first element is the current value.
	– The second element is a setter function.
* Use the current value however you see fit.
* When you want to update the state, call the setter with either a function or a plain value.

___


#### Importing and using a Hook

`useState` is a hook. Hook is an umbrella term for a new kind of special function that exists in React 16.8 and forward. React comes with a number of built-in hooks, and they are hooks because React says so.

In modern React, it’s now a convention that any function starting with the word `use*` is a hook, and non-hooks should never start with that word.

Hooks are named like that because they are hooks from your component to the “insides” of the React machinery. You can do some magic things that aren’t possible without having this extra access.

React comes with 15 hooks (as of React 18), which are low-level units that can be combined to create all sorts of advanced components. New built-in hooks can be added to the React API over time.


#### Rules of Hooks


When you use a hook in a component, you must always use that hook. By “always use,” we mean that the same hook must always be called every time the component renders, that is, every time the component definition function runs. 

This means that you can’t conditionally run a hook, for example, by putting it inside an if block or include it after an optional return statement.


Here the state is being initialized if a condition is true, This is not allowed since it is not called every time
```jsx
function Counter({ isVisible }) 
{
	if( !isVisible )
	{
		return null;
	}
	const [ counter, setCounter ] = useState(0);
	return(
	...);
}
```

Hence all hooks need to be put before attempting to return anything in a component.

```jsx
function Counter({ isVisible }) 
{
	const [ counter, setCounter ] = useState(0);
	
	if( !isVisible )
	{
		return null;
	}

	return(
	...);
}
```


so you can never conditionally run a hook. not run it in a loop, or call a hook inside a callback or event handler. It has to run directly in the component body when called.

___

#### Initializing the state

When you call `useState`, you must pass an initial value; if not, the initial value is assumed to be `undefined`. Only the value that you pass to useState the first time
around for each component instance matters. When your hook re-renders for whatever reason, the initial value is ignored.

Every state has an initial value. Our counter had an initial value of 0, but it didn’t need to be 0, of course.

Creating different variable counters with different start values
```jsx
import { useState } from 'react';

function Counter( {start} )
{
	const [counter, setCounter] = useState(start);
	
	return(
		<main>
			<p>Clicks : {counter}</p>
			<button 
				onClick={() => setCounter( (value) => value+1 )}>
				Increment </button>
		</main>
	);
}

function App()
{
	return (
		<>
			<Counter start={0} />
			<Counter start={123} />
			<Counter start={-64} />
		</>
	);
}
export default App;
```

The most common dynamic initial value is to use a property.

The following are other common static initial values besides numbers:
* true or false for Booleans—If your menu is hidden until a button is clicked, the `isMenuVisible` state is initialized to false.
* Empty string, `""`—If you have an input for a login email address, you’ll initialize your state to the empty value so the input is empty until the user starts typing.
* null—If you have a complex value that hasn’t been set to anything yet, null is the perfect placeholder value for indicating that no value exists yet.


You could also initialize your state to a value from a cookie or similar local storage.

For a login form, you could initialize the email address state with the last known email address used in this same form as stored in a cookie.

___

ONLY THE FIRST INITIAL VALUE MATTERS

only the first value passed to useState is used as the value for the state. If the initial value changes in a subsequent render, the state never updates. This is both good and bad.

It’s possible to have a state value update based on a property, but that requires
other hooks—in particular, the `useEffect` hook.


___

#### Initializer Function

There are times when you want to set the initial value to the result of some calculation.

```jsx
function Password() {
	const [password, setPassword] = useState(generatePassword());
	...
}
```

this `generatePassword()` function will actually be called on every render (because it’s executed on every render), while the return value will be ignored on every render except the first, as just explained.


For this purpose, the initial value can instead be a function that returns the initial value. In such a setup, the initial value function will only be invoked the first time around and will be ignored for future renders,

```jsx
const [password, setPassword] = useState( () => generatePassword() );

// or it can be passed as is since it is a function
const [password, setPassword] = useState(generatePassword);

// if there is argument like length
const [password, setPassword] = useState( () => generatePassword(12) );
```

We don’t actually call `generatePassword` in this instance. We rather instruct the hook to call the function itself only when it needs to (which is only the first time around).

___

#### Initializing to a Function

What if your state is a function? If we pass a function to the initial value, it will be called, so how can we store a function as the initial value? We make another function that returns the first one.

```jsx
const OPERATORS = {
	ADDITION: (a, b) => a + b,
	SUBTRACTION: (a, b) => a - b,
	PRODUCT: (a, b) => a * b,
};

function Calculator()
{
	const [operator, setOperator] = useState(OPERATORS.ADDITION);
	...
}
```
This doesn't work, the function will be called and the initializer is set to NaN since the function returns NaN when no argument was passed for calculation.

We need a function that returns the operator function.
```jsx
function Calculator()
{
	const [operator, setOperator] = useState( () => OPERATORS.ADDITION);
	...
}
```

___

#### Destructuring the state value and setter

When we need a stateful component, we use the useState hook. This hook returns a
value, which we’ve destructured into a state value and a setter function like this:
```jsx
const [value, setter] = useState(initial);
```

This is as close to mandatory as it gets. Other hooks work in similar ways, and you just have to get used to this notation.

___

#### useState return value

The hook returns an array with two elements. The first element is the current value of the state, and the second element is the setter function.

Many things can be done with the array but the recommended and most common way is to destructure
the array directly in the assignment of the return value to a variable and name the two returned values as we see fit.

```jsx
const [counter, setCounter] = useState(0);
```

The only thing to think about here is the naming of the two destructured variables.

#### Using the state value

The state value returned by the useState hook is whatever you set it to. You can change the type, complexity, and so on. You have full control over the value. The value will start at whatever you pass in as the initial value, and from then on, it will be whatever you pass to the setter function.

The counter is initialized to zero and then is changed to a string.
```jsx
import { useState } from 'react';

function Counter()
{
	const [counter, setCounter] = useState(0);
	
	return(
		<main>
			<p>Clicks : {counter}</p>
			<button 
				onClick={() => setCounter("hi there")}>
				Increment </button>
		</main>
	);
}
```
The state was changed but this will actually work.


___

#### Setting the state

Setting the state is fairly straightforward in that it works exactly like setting the initial value, with all the same quirks and workarounds. We can update the state either by setting it to a static value or by using an update function that returns the new value to be set.

simple accordion component where you can expand and collapse the contents.

```jsx
import { useState } from 'react';

function Accoedion()
{
	const [isExpanded, setExpanded] = useState(false);
	
	return(
		<main>
			<h2 style={ {display: "flex", gap:"6px"} } >
				Secret password
				<button onClick={ ()=> setExpanded(fasle) }>
				-
				</button>
				<button onClick={ ()=> setExpanded(true) } >
				+
				</button>
			</h2>
			{ isExpanded && (
				<p>
					Password: <code>hunter2</code>
				</p>
			)}
		</main>
	);
}

function App()
{
	return <Accordion />;
}

export default App;
```

This component is an example of using the setter with a static value. The minus button always sets the state value to false no matter how many times you click it. Because we set it to a fixed value, we don’t need to look at the current value.

___

#### Setting using an Update Function

If you use an update function, it will be passed the current state as an argument.

```jsx
const [counter, setCounter] = useState(0);
...
<button onClick={() => setCounter((value) => value + 1)}>
```

#### Setting to a Function

```jsx
import { useState } from "react";

const PLUS = (a,b) => a+b;
const MINUS = (a,b) => a-b;
const MULTIPLY = (a,b)=> a*b;

function Calculator({a, b})
{
	const [operator, setOperator] = useState( ()=> PLUS );
	
	return (
		<main>
			<h1>Calculator</h1>
			
			<button onClick= { ()=> setOperator( ()=>PLUS) } >
			Plus
			</button>
			
			<button onClick= { ()=> setOperator( ()=>MINUS) } >
			Minus
			</button>
			
			<button onClick= { ()=> setOperator( ()=>MULTIPLY) } >
			Multiply
			</button>
			
			<p>
				Result of applying operator to {a} and {b}:
				<code>{operator(a,b)}</code>
			</p>
		</main>
	); 
}

function App() {
	return <Calculator a={7} b={4} />
}
export default App;
```

The state value can be called now as a function to take the variables.

___

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

