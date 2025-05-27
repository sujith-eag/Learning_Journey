

Using vite to set up custom built project setup
```bash
npm create vite@latest app-name

cd app-name

npm install # to install all dependencies

npm run dev

# http://localhost:5173
```

JavaScript allows you to add interactivity to your website since, with JavaScript, you can react to user events and manipulate the page after it is loaded. This is extremely valuable as it allows you to build highly interactive web user interfaces (UIs).

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


## React manipulating DOM

React (the library) splits its core logic across two main packages:
•The main react package
•The react-dom package

The main react package is a third-party JavaScript library that needs to be imported into a project to use React’s features (like JSX or state) there. It’s this package that creates this virtual DOM and
derives the current UI state. But you also need the react-dom package in your project if you want to manipulate the DOM with React.

It’s the react-dom package that will produce the actual DOM
instructions that will select, update, delete, and create DOM elements.

The react-dom package, specifically the react-dom/client part of that package, acts as a “translation bridge” between your React code, the internally generated virtual DOM, and the browser with its actual DOM that needs to be updated.

This split exists because you can also use React with other target environments. Well-known alternative to the DOM (i.e., to the browser) would be React Native, which allows developers to build native mobile apps with the help of React.


___

it’s also becoming more and more popular to build full-stack React apps, where frontend and backend code are merged. Modern React frameworks like Next.js simplify the process of building such web apps.



## Creating a React Project with Vite

To work with React, the first step is the creation of a React project. The official documentation recommends using a framework like Next.js. But while this might make sense for complex web applications. Next.js and other frameworks introduce their own concepts and syntax. As a result, learning React can quickly become
frustrating since it can be difficult to tell React features apart from framework features. 

Vite is an open-source development and build tool that can be used to create and run web development projects based on all kinds of libraries and frameworks – React is just one of the many options.

pre-processing step is required.

Vite creates projects that come with a built-in, preconfigured build process that, in the case of React projects, takes care of the JSX code transpilation. It also provides a development web server that runs locally on your system and allows you to preview the React app while you’re working on it.

___

```
npm create vite@latest my-react-project
```

Once executed, this command will prompt you to choose a framework or library you want to use for this new project. You should choose React and then JavaScript.

This command will create a new subfolder with a basic React project setup (i.e., with various files and folders) in the place where you ran it.


the project creation command does not install any required dependencies such as the React library packages. For that reason, you must navigate into the created folder in your system terminal or command prompt (via cd my-react-project) and install these packages by running
```
npm install
```

Project setup is complete once the installation finishes, and to view created react application the development server can be started with
```
npm run dev
```

___

every new Vite-based React project contains a couple of key files and folders:

* A src/ folder, which contains the main source code files for the project:
	* A main.jsx file, which is the main entry script file that will be executed first
	* An App.jsx file, which contains the root component of the application.
	* Various styling (*.css) files, which are imported by the JavaScript files
	* An assets/ folder that can be used to store images or other assets that should be used in your React Code.
* A public/ folder, which contains static files that will be part of the final website (e.g., a favicon)
* An index.html file, which is the single HTML page of this website.
* package.json and package-lock.json are files that list and define the third-party dependencies of the project
* Other project configuration files (e.g., .gitignore for managing Git file tracking)
* A node_modules folder, which contains the actual code of the installed third-party packages

>[!note]
>It’s worth noting that App.jsx and main.jsx use .jsx as a file extension, not .js. This is a file extension that's enforced by Vite for files that do not just contain js but jsx code

___

