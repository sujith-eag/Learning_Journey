
# Events

Since listening to events and triggering actions upon events is an extremely common requirement, React has a built-in solution. You can attach event listeners directly to the JSX elements to which they
belong.

```jsx{16}
function EmailInput() {
	let errorMessage = '';
	
	function evaluateEmail(event) {
		const enteredEmail = event.target.value;
		if( enteredEmail.trim()==='' || !enteredEmail.includes('@')) {
			errorMessage = 'The entered email address is invalid.';
		} else {
			errorMessage = '';
		}
	};
	return (
		<div>
			<input
				placeholder="Your email"
				type="email"
				onBlur={evaluateEmail}
			/>
			<p>{errorMessage}</p>
		</div>
	);
};
```

This code will not update the UI, but at least the event is handled properly.

The onBlur prop was added to the built-in input element. This prop is made available by React.

React exposes all standard events that can be connected to DOM elements as onXYZ props (where XYZ is the event name, such as blur or click, starting with a capital character). You can react to the blur event by adding the onBlur prop. You could listen to a click event via the onClick prop.


These props require pointer to the function that should be executed when the event occurs.


>[!important]
>There’s a subtle difference between evaluateEmail and evaluateEmail(). The first is a pointer to the function; the second actually executes the function (and yields the return value, if any)


## State

State is a React feature that allows developers to update internal data and trigger a UI update based on such data adjustments.

```jsx{1,4,9,10}
import { useState } from 'react';

function EmailInput() {
	const [ errorMessage, setErrorMessage ] = useState('');
	
	function evaluateEmail(event) {
		const enteredEmail = event.target.value;
		if( enteredEmail.trim()==='' || !enteredEmail.includes('@')) {
			setErrorMessage('The entered email address is invalid.');
		} else {
			setErrorMessage('');
		}
	};
	return (
		<div>
			<input
				placeholder="Your email"
				type="email"
				onBlur={evaluateEmail}
			/>
			<p>{errorMessage}</p>
		</div>
	);
};
```

`useState()` is a Hook. Hooks are special functions that can only be used inside of React components.

### useState()

By calling `useState()` inside a component function, you register some data with React. It’s a bit like defining a variable or constant in JavaScript. But React will track the registered value internally, and whenever it is updated, React will re-evaluate the component function in which the state was registered.

state is data, which, when changed, should force React to re-evaluate a component and update the UI if needed. If no update is needed, React ends the component re-evaluation without updating the DOM.

___

Process starts with calling useState() inside a component. This creates a state value and ties it to a specific component. An initial state value is registered by simply passing it as a parameter.

```jsx
const [errorMessage, setErrorMessage] = useState('');
```
useState() does not just accept a parameter value. It also returns a value: an array with exactly two elements.

array destructuring, is used to retrieve values from an array and immediately assign them to variables or constants.

The first element is always the current state value, and the second element is a function that you can call to set the state to a new value.


State-updating function sets a new value; it also informs React that a state value changed and that the UI might therefore be
in need of an update.

React will re-execute (re-evaluate) a component function if a state-updating function is called in the component function or some parent component function. useState() is also called
again and hence a new array with two new elements is returned by React. The first array element is still the current state value.

### Naming Conventions

The first element (that is, the current state value) should be named such that it describes what the state value is all about. Examples would be enteredEmail, userEmail, providedEmail, email.

The second element (that is, the state-updating function) should be named such that it becomes clear that it is a function and that it does what it does. setEnteredEmail or setEmail.

### Allowed State value types

Besides managing primitive value types, you can also store and update reference data types such as objects and arrays.

You can even switch the value type at runtime, to store a number as the initial state value and update it to a string at a later point in time.

## Multiple State Values

There are two main ways of doing that:
1. Use multiple state slices (multiple state values)
2. Using one single, big state object

### Using Multiple State Slices

You can manage multiple state values (also often called state slices) by simply calling useState() multiple times in your component function.

```jsx
function LoginForm() 
{
	const [enteredEmail, setEnteredEmail] = useState('');
	const [enteredPassword, setEnteredPassword] = useState('');

	function handleUpdateEmail(event) 
	{
		setEnteredEmail(event.target.value);
	};
	function handleUpdatePassword(event) 
	{
		setEnteredPassword(event.target.value);
	};

	return (
		<form>
			<input
				type="email"
				placeholder="Your email"
				onBlur={handleUpdateEmail} />
			
			<input
				type="password"
				placeholder="Your password"
				onBlur={handleUpdatePassword} />
		</form>
	);
};
```

### Merged State Objects

Instead of calling useState() for every single state slice, you can go for one big state object that combines all the different state values:

```jsx
function LoginForm() 
{
	const [userData, setUserData] = useState({
		email: '',
		password: ''
	});

	function handleUpdateEmail(event) {
		setUserData({
			email: event.target.value,
			password: userData.password
		});
	};
	
	function handleUpdatePassword(event) {
		setUserData({
			email: userData.email,
			password: event.target.value
		});
	};
// ... code omitted
};
```

The first element of the returned array is now just an object instead of a string. The object contains two properties: email and password.

>[!important]
>When calling the state-updating function, you must always set all properties the object contains, even the ones that didn’t change. This is required to tell React which new state value should be stored internally.


If you provide an object that contains only the properties that changed, all other properties will be lost since the previous state object is replaced by the new one, which contains fewer properties.







### Updating state based on Previous State

setting a state value to a new value that is (at least partially) based on the previous state is a common task.

```jsx
function Counter() {
	const [counter, setCounter] = useState(0);
	
	function handleIncrement() {
		setCounter(counter + 1);
	};
	
	return (
		<>
			<p>Counter Value: {counter}</p>
			<button onClick={handleIncrement}>Increment</button>
		</>
	);
};
```

Upon every click, the counter state value is incremented by 1.

This component would work, but is actually violating an important best practice and recommendation: state updates that depend on some previous state should be performed with the help of a function that’s passed to the state-updating function.

```jsx
function Counter() {
	const [counter, setCounter] = useState(0);
	
	function handleIncrement() {
		setCounter( prevCounter => prevCounter + 1 );
		// setCounter(function(prevCounter){ return prevCounter + 1; }); 
	};
	
	return (
		<>
			<p>Counter Value: {counter}</p>
			<button onClick={handleIncrement}>Increment</button>
		</>
	);
};
```

A function is passed as an argument to the state-updating function, React will call that function for you and pass the latest state value to that function.

Therefore, you should provide a function that accepts at least one parameter: the previous state value. This value will be passed into the function automatically by React when React executes the function (which it will do internally).

The function should then also return a value—the new state value that should be stored by React.

```jsx
function LoginForm() 
{
	const [userData, setUserData] = useState({
		email: '',
		password: ''
	});

	function handleUpdateEmail(event) {
		setUserData( prevData=> ({
			email: event.target.value,
			password: prevData.password	
		})
		);
	};
	
	function handleUpdatePassword(event) {
		setUserData( prevData => ({
			email: prevData.email,
			pasword: event.target.value
		}));
	};
// ... code omitted
};
```

>[!important]
>You should always pass a function to the state-updating function if the new state depends on the previous state. Otherwise, if the new state depends on some other value (for instance, user input), directly passing the new state value as a function argument is absolutely fine and recommended.


## Two-Way Binding

Two-way binding is a concept that is used if you have an input source (typically an `<input>` element) that sets some state upon user input (for instance, upon the change event) and outputs the input at the same time.

```jsx
function NewsletterField() {
	const [email, setEmail] = useState('');
	
	function handleUpdateEmail(event) {
		setEmail(event.target.value);
	};

	return (
		<>
			<input
				type="email"
				placeholder="Your email address"
				value={email}
				onChange={handleUpdateEmail} />
		</>
	);
};
```

The component does not just store the user input (upon the change event, in this case) but that the entered value is also output in the `<input>` element (via the default value prop) thereafter.

>[!note]
>This might look like an infinite loop, but React deals with this and ensures that it doesn’t become one. Instead, this is what’s commonly referred to as two-way binding as a value is both set and read from the same source.

___

A button in the component that, when clicked, should clear the entered email address.

```jsx
function NewsletterField() {
	const [email, setEmail] = useState('');

	function handleUpdateEmail(event) {
		setEmail(event.target.value);
	};

	function handleClearInput() {
		setEmail(''); 
		// reset email input (back to an empty string)
	};
	
	return (
		<>
			<input
				type="email"
				placeholder="Your email address"
				value={email}
				onChange={handleUpdateEmail} />
			
			<button onClick={handleClearInput}>Reset</button>
		</>
	);
};
```

Without two-way binding, the state would be updated, but the change would not be reflected in the `<input>` element. There, the user would still see their last input.

## Deriving Values from State

Passing state via props to repeat what was typed

```jsx
function Repeater() {
	const [ userInput, setUserInput ] = useState('');

	function handleChange(event) {
		setUserInput(event.target.value);
	};
	
	return(
		<>
			<input type="text" onChange={handleChange} />
			<p>You entered: {userInput}</p>
		</>
	);
};
```

instead of simply repeating what the user entered, you could count the number of entered characters and show that information to the user:

```jsx
function Repeater() {
	const [ userInput, setUserInput ] = useState('');

	function handleChange(event) {
		setUserInput(event.target.value);
	};

	const numChars = userInput.length;
	
	return(
		<>
			<input type="text" onChange={handleChange} />
			<p>Characters entered: {numChars}</p>
		</>
	);
};
```

You’re not limited to working with state values only. You can manage some key value as state (that is, the value that will change) and derive other values based on that state value.

## Forms and Form Submission

when adding input validation (that is, checking entered values), you might want to use individual input events to give website users useful feedback while they’re typing.

But it’s also quite common to react to the overall form submission. To combine the input from various input fields and send the data to some backend server.

`onSubmit` prop can be added to `<form>` elements to assign a function that should be executed once a form is submitted. To then handle the submission with React and JavaScript, you must ensure that the browser won’t do its default thing and generate (and send) an HTTP request automatically.

As in vanilla JavaScript, this can be achieved by calling the `preventDefault()` method on the automatically generated event object.


```jsx
function NewsletterSignup() {
	const [email, setEmail] = useState('');
	const [agreed, setAgreed] = useState(false);

	function handleUpdateEmail(event) {
		// could add email validation here
		setEmail(event.target.value);
	};
	
	function handleUpdateAgreement(event) {
		setAgreed(event.target.checked); 
		// checked is a default JS boolean property
	};

	function handleSignup(event) {
		event.preventDefault(); 
		// prevent browser default of sending a Http request
		const userData = {userEmail: email, userAgrees: agreed};
		// doWhateverYouWant(userData);
	};
	
	return (
		<form onSubmit={handleSignup}>
			<div>
				<label htmlFor="email">Your email</label>
				<input type="email" id="email" onChange={handleUpdateEmail}/>
			</div>

			<div>
				<input type="checkbox" id="agree" onChange={handleUpdateAgreement}/>
				<label htmlFor="agree">Agree to terms and conditions</label>
			</div>
		</form>
	);
};
```

>[!important]
>`htmlFor` is a special prop, built into React and the core JSX elements it provides. It can be added to `<label>` elements in order to set the for attribute for these elements. The reason it is called `htmlFor` instead of just `for` is that, JSX looks like HTML but isn’t HTML. It’s JavaScript under the hood.
> 
>In JavaScript, for is a reserved keyword for `for` loops. To prevent problems, the prop is therefore named `htmlFor`.

Using onSubmit (combined with preventDefault()) for handling form submissions is a very common way of dealing with user input and forms in React.

Alternatively you can use a React feature called Form Actions.

## Lifting State up

Common scenario and problem: you have two components in your React app and a change or event in component A should change the state in component B.

```jsx
function SearchBar() {
	const [searchTerm, setSearchTerm] = useState('');

	function handleUpdateSearchTerm(event) {
		setSearchTerm(event.target.value);
	};
	
	return <input type="search" onChange={handleUpdateSearchTerm} />;
	};
	
	function Overview() {
		return <p>Currently searching for {searchTerm}</p>;
	};
	
	function App() {
		return (
			<>
				<SearchBar />
				<Overview />
			</>
	);
};
```

the Overview component should output the entered search term. However, the search term is actually managed in another component—namely, the SearchBar component.

Having multiple components depend on some shared piece of state is therefore a scenario you will face frequently when working with React.

This problem can be solved by lifting state up. When lifting state up, the state is not managed in either of the two components that use it—neither in Overview, which reads the state, nor in SearchBar, which sets the state—but in a shared ancestor component instead.

it is managed in the closest shared ancestor component.

the App component is the closest (and, in this case, only) ancestor component of both SearchBar and Overview.

>[!important]
>State is lifted by using props in the components that need to manipulate (that is, set) or read state, and by registering state in the ancestor component that is shared by the two other components.

```jsx
function App() {
	const [ searchTerm, setSearchTerm ] = useState('');

	function handleUpdateSearchTerm(event) {
		setSearchTerm(event.target.value);
	};
	
	return (
		<>
			<SearchBar onUpdateSearch ={handleUpdateSearchTerm} />
			<Overview currentTerm={searchTerm} />
		</>
	);
};

function SearchBar( {onUpdateSearch} ) {
	return (
		<input type="search" onChange={onUpdateSearch} />
	);
};

function Overview( {currentTerm} ) {
	return (
		<p>Currently searching for {currentTerm}</p>
	);
}

```


The state is now managed inside of the shared ancestor and App component, and the two other components get access to it via
props.

Three key things are happening in this example:
1. The SearchBar component receives a prop called onUpdateSearch, whose value is a function. (A function created in the App component and passed down to SearchBar from App).
2. The onUpdateSearch prop is then set as a value to the onChange prop on the `<input>` element inside of the SearchBar component.
3. The searchTerm state (that is, its current value) is passed from App to Overview via a prop named currentTerm.

____

Since the child and descendent components are also re-evaluated by React when state changes in a
component, changes in the App component will also lead to the SearchBar and Overview components
being re-evaluated. Therefore, the new prop value for searchTerm will be picked up, and the UI will
be updated by React.


## Summary and Key Takeaways

* Event handlers can be added to JSX elements via `on[EventName]` props (for example, onClick, onChange).
* Any function can be executed upon (user) events.
* In order to force React to re-evaluate components and (possibly) update the rendered UI, state must be used.
* State refers to data managed internally by React, and a state value can be defined via the useState() Hook.
* React Hooks are JavaScript functions that add special features to React components (for example, the state feature, in this chapter).
* useState() always returns an array with exactly two elements:
* The first element is the current state value.
* The second element is a function to set the state to a new value (the state-updating function).
* When setting the state to a new value that depends on the previous value, a function should be passed to the state-updating function. This function then receives the previous state as a parameter (which will be provided automatically by React) and returns the new state that should be set.
* Any valid JavaScript value can be set as state—besides primitive values such as strings or numbers. This also includes reference values such as objects and arrays.
* If state needs to change because of some event that occurs in another component, you should lift the state up and manage it on a higher, shared level (that is, a common ancestor component).

____

