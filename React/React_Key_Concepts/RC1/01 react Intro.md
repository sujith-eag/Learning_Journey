
Using vite to set up custom built project setup
```bash
npm create vite@latest app-name

cd app-name

npm install # to install all dependencies

npm run dev

# http://localhost:5173
```

JavaScript allows you to add interactivity
to your website since, with JavaScript, you can react to user events and manipulate the page after it is
loaded. This is extremely valuable as it allows you to build highly interactive web user interfaces (UIs).

____

### libraries and framework

React is “The library for web and native user interfaces.”

pragmatic definition of a library is that it’s a collection of functionalities that you can use
in your code to achieve results that would normally require more code and work from your side.
Libraries can help you write more concise and possibly also less error-prone code and enable you to
implement certain features more quickly.
React is such a library

___

React simplifies the creation and management of such UIs by moving from an imperative to a declar-
ative approach.

To understand it, the idea behind “imperative versus declarative
approaches,” and why you might want to use React instead of just vanilla JavaScript, it’s helpful to take
a step back and evaluate how vanilla JavaScript works.

```js
const buttonElement = document.querySelector('button');
const paragraphElement = document.querySelector('p');

function updateTextHandler() {
	paragraphElement.textContent = 'Text was Changed';
}

buttonElement.addEventListner('click', updateTextHandler);
```

code is written with vanilla JavaScript and, as a consequence, imperatively. This means that you write instruction after instruction, and you describe every step that needs to be taken in detail.

that is how most programming languages work: you define a series of steps that must be executed in order. It’s an approach that makes a lot of sense because the order of code execution shouldn’t be random or unpredictable.


___

However, when working with UIs, this imperative approach is not ideal. Indeed, it can quickly become
cumbersome because, as a developer, you have to add a lot of instructions that, despite adding little
value, cannot simply be omitted. You need to write all the Document Object Model (DOM) instruc-
tions that allow your code to interact with elements, add elements, manipulate elements, and so on.

Your core business logic (e.g., deriving and defining the actual text that should be set after a click)
therefore often makes up only a small chunk of the overall code. When controlling and manipulating
web UIs with JavaScript, a huge chunk (often the majority) of your code is frequently made up of DOM
instructions, event listeners, HTML element operations, and UI state management.

```jsx
import { useState } from 'react';

function App() {
	const [ outputText, setOutputText ] = useState('Initial text');

	function updateTextHandler() {
		setOutputText('Text was changed');	
	}

	return (
		<>
			<button onClick={updataTextHandler}>
				Click to change text
			</button>
			<p>{outputText}</p>
		</>
	);
}
```

>[!note]
>JSX (i.e., JavaScript extended to include XML-like syntax).
>JSX code will work because of a pre-processing (or transpilation) step that’s part of the build workflow of every React project.


___

the “declarative approach” used by React: you write your JavaScript logic (e.g., functions that should eventually be executed), and you combine that logic with the HTML code that should trigger it or that is affected by it.

`outputText` is some state managed by React. In the code, the `updateTextHandler` function is triggered upon a click, and the `outputText` state value is set to a new string value ('Text was changed!') with the help of the `setOutputText` function.

The general idea, though, is that the state value is changed and, since it’s being referenced in the last paragraph (`<p>{outputText}</p>`), React outputs the current state value in that place in the actual DOM (and hence, on the actual web page). React will keep the paragraph updated, and therefore, whenever `outputText` changes, React will select this paragraph element again and update its `textContent` automatically.

___

```jsx
import { useStae } from 'react';

function validateEmail(enteredEmail) {
	const promise = new Promise( function(resolve, reject) 
	{
		if(enteredEmail == 'test@test.com') 
		{
			reject(new Error('Emain exists already'));
		}
		else
		{
			resolve();
		}
	});
	return promise;
}

function validatePassword(enteredPassword) {
	if(enteredPassword.trim().length < 6) {
		throw new Error('Invalid Password - must be least 6 characters');
	}
}

function App() {
	const [emailIsValid, setEmailIsValid] = useState(true);
	const [passwordIsValid, setPasswordIsValid] = useState(true);
	const [modalData, setModalData] = useState(null);
	
	async function validateInputHandler(inputType, input) {
		const enteredValue = event.target.value;
		
		let validateFn = validateEmail;
		if(inputType == 'password') {
			validateFn = validatePassword;
		}
		
		let isValid = true;
		
		try {
			await validateFn(enteredValue);
		} catch (error) {
			isValid = false;
		}
		
		if(inputType == 'email') {
			setEmailIsValid(isValid);
		} else {
			setPasswordIsValid(isValid);
		}
	}	
	function submitFormHandler(event) {
		event.preventDefault();
		
		let title = 'An error occusrred';
		let message = 'Invalid input values';
		
		if (emailIsValid && passwordIsValid) {
			title = 'success!';
			message = 'User created successfully';
		}
		
		setModalData( {
			title: title,
			message: message,
		});
	}
	function closeModal() {
		setModalData(null);
	}
	
	return (
		<>
			{modalData && <div className='backdrop' ocClick={closeModal}></div>}
			{modalData && (
				<aside className= 'modal'>
					<header>
						<h2>{modalData.title}</h2>
					</header>
					<section>
						<p>{modalData.messgae}</p>
					</section>
					<section>
						<button onClick={closeModal}>Okay</button>
					</section>
				</aside>
			)}
			
			<header>
				<h1>Create a New Account</h1>
			</header>
			<main>
				<form onSubmit={submitFormHandler}>
					<div className='form-control'>
						<label htmlFor='email'>Email</label>
						<input
							type='email'
							id='email'
							onBlur={validateInputHandler.bind(null, 'email')}
						/>
						{!emailIsValid && <p>This email is already taken!</p>}
					</div>
					<div className='form-control'>
						<label htmlFor='password'>Password</label>
						<input
							type='password'
							id='password'
							onBlur={validateInputHandler.bind(null, 'password')}
						/>
						{!passwordIsValid && (
							<p>password must be ateast 6 characters long</p>
						)}
					</div>
					<button>Create User</button>
				</form>
			</main>
			
			<footer>
				<p>(c)Sujith Kumar</p>
			</footer>
		</>
	);
}

export default App;
```

In the react section of the code there are absolutely no operations that would select DOM elements, create or insert DOM elements,
or edit DOM elements.

