
# Refs

Instead of manipulating the DOM or reading values from DOM elements manually, you can use React to describe the desired state. React then takes care of the steps needed to achieve
this desired state.

However, there are scenarios and use cases wherein, despite using React, you still want to be able to directly reach out to specific DOM elements, to read a value entered by a user into an
input field, or if you’re not happy with the position of a newly inserted element in the DOM that was chosen by React.

React provides certain functionalities that help you in exactly these kinds of situations: Portals and Refs.

## World without Refs


The only reason for using the enteredEmail state in the example is to read the entered value ad does nothing else. Adding the extra event listener and state, as well as adding the function to update the state whenever the change event is triggered, is quite a bit of boilerplate code for one simple task. Also it re-renders on each key stroke.

```jsx
function EmailForm() {
	const [enteredEmail, setEnteredEmail] = useState('');
	
	console.log(enteredEmail);

	function handleUpdateEmail(event) {
		setEnteredEmail(event.target.value);
	}
	
	function handleSubmitForm(event) {
		event.preventDefault();
		// could send enteredEmail to a backend server
	}
	
	return (
			<form className={classes.form} onSubmit={handleSubmitForm}>
			<label htmlFor="email">Your email</label>
			<input type="email" id="email" onChange={handleUpdateEmail} />
			<button>Save</button>
		</form>
	);
}
```

The basic logic would be 
```js
const emailInput = document.getElementById('email');
const enteredValue = emailInput.value;
```

or
```js
const enteredValue = document.getElementById('email').value;
```

The problem with this kind of code is that it does not use React. Don’t start blending your own vanilla JavaScript code that accesses the DOM into the React code.

React would not be aware of your changes in that case; the actual rendered UI would not be in sync with React’s assumed UI.


## Refs

To still allow you to get hold of DOM elements and read values, as shown above, React gives you a special concept that you can use: Refs.

it’s a feature that allows you to store references to values like DOM elements inside react components.

Refs can be created using a special React Hook called the `useRef()` Hook to generate ref object.

```jsx
import { useRef } from 'react';

function EmailForm(){
	const emailRef = useRef(null);
	// other code ..
};
```

This generated Ref object, `emailRef` is initially set to null but can then be assigned to any JSX element. This assignment is done via a special prop (`ref` prop) that is automatically supported by every JSX element:

```jsx
return(
	<form className={classes.form} onSubmit={handleSubmit}>
		<label htmlFor='email'>Your email</label>
		<input 
			ref={emailRef},
			type='email',
			id='email'
		/>
	</form>
);
```

`useRef()` receives null as an initial value since it’s technically not yet assigned to the DOM element when the component function executes for the first time. It’s only after that initial component render cycle that the connection will be established and value stored in Ref will be the DOM object.

>[!note]
>To get hold of the connected element, you must access a special `current` prop on the created Ref object. This is required because React stores the value assigned to the Ref object in a nested object, accessible via the `current` property.

```jsx
function handleSubmit(event){
	event.preventDefault();
	const enteredEmail = emailRef.current.value;
	// ....
};
```

`emailRef.current` yields the underlying DOM object.


## Refs versus State

you can read the value from the DOM element without having to use `useState()` and an event listener.

```jsx
function EmailForm(){
	const emailRef = useRef(null);
	
	function handleSubmit(event){
		event.preventDefault();
		const enteredEmail = emailRef.current.value;
		// ....
	}
	
	return(
		<form className={classes.form} onSubmit={handleSubmit}>
			<label htmlFor='email'>Your email</label>
			<input 
				ref={emailRef},
				type='email',
				id='email'
			/>
		</form>
	);
}
```


Refs can replace state if you’re just accessing some value to read it when some function (a form submit handler function, for example) is executed. As soon as you need to change values and those changes must be reflected in the UI (for example, by rendering some conditional content), Refs are out of the game.

if, besides getting the entered value, you’d also like to reset (i.e., clear) the email input after the form was submitted, you should use state again.

>[!note]
>`emailRef.current.value = '';`
>This is possible with ref also but shouldn't be done. Only react should manipulate the DOM


```jsx
function EmailForm(){
	const [enteredEmail, setEnteredEmail] = useState('');

	function handleEmailUpdate(event){
		setEnteredEmail(event.target.value);
	}
	
	function handleSubmit(event){
		event.preventDefault();
		const enteredEmail = emailRef.current.value;
		// ....
		setEntetrdEmail('');
	}
	
	return(
		<form className={classes.form} onSubmit={handleSubmit}>
			<label htmlFor='email'>Your email</label>
			<input 
				type='email',
				id='email'
				onChange={handleEmailUpdate},
				value={enteredEmail}
			/>
			<button>Save</button>
		</form>
	);
}
```

## Refs for more than DOM Access

Refs are more than just “element connection bridges;” they are objects that can be used to store all kinds of values—not just pointers at DOM objects.

This can be useful for storing data that should “survive” component re-evaluations. When the function is executed again, any data stored in function-scoped variables would be lost. Refs are not reset or cleared when the surrounding component function is executed again.

>[!important]
>Changing Ref values does not trigger component functions to be executed again—state, on the other hand, does

Therefore, if you have data that should survive component re-evaluations but should not be managed as state (because changes to that data should not cause the component to be re-evaluated when changed), you could use a Ref:

```jsx
const passwordRetries = useRef(0);

// later in the component ...
passwordRetries.current = 1; // changed from 0 to 1

// later ...
console.log(passwordRetries.current); 
// prints 1, even if the component changed
```

This is not a feature that’s used frequently, but it can be helpful from time to time. In all other cases use normal state value.


## Refs in Custom Components

You can expose features (for example, functions or state values) of a component to other components via Refs. Refs can essentially be used as a communication device between two components, just as they were used as a communication device with a DOM element in the previous sections.

Conveniently, your custom components can receive a ref as a regular prop:

Preference Component
```jsx
function Preferences(props){
	const { ref } = props // extracting ref prop
	
	const [wantsNewProdInfo, setWantsNewProdInfo] = useState(false);
	const [wantsProdUpdateInfo, setWantsProdUpdateInfo] = useState(false);
	
	function handleChangeNewProdPref () {
		setWantsNewProdInfo((prevPref) => !prevPref);
	}
	
	function handleChangeUpdateProdPref() {
		setWantsProdUpdateInfo((prevPref) => !prevPref);
	}

	function reset() {
		setWantsNewProdInfo(false);
		setWantsProdUpdateInfo(false);
	}
	
	ref.current.reset = reset;
	
	ref.current.selectedPreferences = {
		newProductInfo: wantsNewProdInfo,
		productUpdateInfo: wantsProdUpdateInfo,
	};
	
	return (
		<div className={classes.preferences}>
			<label>
				<input
					type="checkbox"
					id="pref-new"
					checked={wantsNewProdInfo}
					onChange={handleChangeNewProdPref}
				/>
				<span>New Products</span>
			</label>
			
			<label>
				<input
					type="checkbox"
					id="pref-updates"
					checked={wantsProdUpdateInfo}
					onChange={handleChangeUpdateProdPref}
				/>
				<span>Product Updates</span>
			</label>
	</div>
});
```

```jsx
function Form() {
	const preferencesRef = useRef({});

	function handleSubmit(event) {
		event.preventDefault();
		
		console.log(preferencesRef.current.selectedPreferences); 
		// reading ref value from Preferences

		preferencesRef.current.reset(); 
		// executing a function stored in Preferences
	}
	
	return (
	<form className={classes.form} onSubmit={handleSubmit}>
		<div className={classes.formControl}>
			<label htmlFor="email">Your email</label>
			<input type="email" id="email" />
		</div>
		<Preferences ref={preferencesRef} />
		<button>Submit</button>
	</form>
	);
}
```

By using Refs like this, a parent component (Form, in this case) is able to interact with some child component (for instance, Preferences) in an imperative way—meaning properties can be accessed and methods called to manipulate the child component (or, to be precise, to trigger some internal functions and behavior inside the child component).

___

### Controlled versus Uncontrolled Components

Allowing user entered values to manipulate the DOM is Uncontrolled.

a component becomes controlled as soon as React manages the state.

the Form and Preferences components, switching to a controlled component approach could look like this:

The Preferences component stops managing the checkbox state and instead receives props from its parent component (the Form component).
```jsx
function Preferences({newProdInfo, prodUpdateInfo, onUpdateInfo}) {
	return (
		<div className={classes.preferences}>
		<label>
			<input
				type="checkbox"
				id="pref-new"
				checked={newProdInfo}
				onChange={onUpdateInfo.bind(null, 'pref-new')}
			/>
			<span>New Products</span>
		</label>
		
		<label>
			<input
				type="checkbox"
				id="pref-updates"
				checked={prodUpdateInfo}
				onChange={onUpdateInfo.bind(null, 'pref-updates')}
			/>
			<span>Product Updates</span>
		</label>
	</div>
	);
};
```

bind() is used on the onUpdateInfo prop (which will receive a function as a value) to pre-configure the function for future execution. bind() is a default JavaScript method that can be called on any JavaScript function to control which arguments will be passed to that function once it’s invoked in the future.

The Form component now manages the checkbox states, even though it doesn’t directly contain the checkbox elements. But it now begins to control the Preferences component and its internal state, hence turning Preferences into a controlled component instead of an uncontrolled one:

```jsx
function Form() {
	const [wantsNewProdInfo, setWantsNewProdInfo] = useState(false);
	const [wantsProdUpdateInfo, setWantsProdUpdateInfo] = useState(false);

	function handleUpdateProdInfo(selection) {
	// using one shared update handler function is optional
	// you could also use two separate functions (passed to Preferences) as props
		if (selection === 'pref-new') {
			setWantsNewProdInfo((prevPref) => !prevPref);
		} else if (selection === 'pref-updates') {
			setWantsProdUpdateInfo((prevPref) => !prevPref);
		}
	}
	
	function reset() {
		setWantsNewProdInfo(false);
		setWantsProdUpdateInfo(false);
	}
	
	function handleSubmit(event) {
		event.preventDefault();
		// state values can be used here
		reset();
	}
	
	return (
	<form className={classes.form} onSubmit={handleSubmit}>
		<div className={classes.formControl}>
			<label htmlFor="email">Your email</label>
			<input type="email" id="email" />
		</div>
		<Preferences
			newProdInfo={wantsNewProdInfo}
			prodUpdateInfo={wantsProdUpdateInfo}
			onUpdateInfo={handleUpdateProdInfo}
		/>
		<button>Submit</button>
	</form>
	);
}
```

The Form component now controls the Preferences component.

____


