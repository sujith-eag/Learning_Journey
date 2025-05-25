
# Component


## Anatomy of Component

Components are reusable building blocks that are combined to compose the final user interface.

Some components are neted inside other components, i.e components are made up of components.



other libraries—both frontend libraries like React or Angular as well as backend libraries and templating engines like EJS (Embedded JavaScript templates)—also embrace components (though the names might differ, you also find “partials” or “includes” as common names).

>[!note]
>EJS is a popular templating engine for JavaScript. It’s especially popular for backend web development with Node.js

```jsx
import { useState } from 'react';

function SubmitButton() {
	const [isSubmitted, setIsSubmitted] = useState(false);
	
	function handleSubmit() {
		setIsSubmitted(true);
	}
	return (
		<button onClick={handleSubmit}>
			{ isSubmitted ? 'Loading...' : 'Submit' }
		</button>
	);
};

export default SubmitButton;
```

You would store a code snippet like this in a separate file (e.g., a file named `SubmitButton.jsx`, stored inside a `/components` folder, which in turn resides in the `/src` folder of your React project) and import it into other component files that need this component.

>[!important]
>Vite enforces the usage of .jsx as a file extension if you’re writing JSX code – storing such code in .js files is not allowed in Vite projects (even though it might work in other React project setups).


```jsx
import SubmitButton from './submit-button.jsx';

function AuthForm() {
	return (
		<form>
			<input type="text" />
		
			<SubmitButton />
		</form>
	);
};

export default AuthForm;
```

The import statements you see are standard JavaScript import statements. In Vite-based projects, you could omit the file extension (.jsx in this case) in the import statement.

>[!note]
>Things like variables, constants, classes, or functions can be exported via export or export default so that they can then be used in other files after importing them there.


When working with React, there are two alternative ways to define components:
* Class-based components (or “class components”): Components defined via the class keyword
* Functional components (or “function components”): Components that are defined via regular JavaScript functions


___

There are a couple of other noteworthy things:
* The component functions carry capitalized names (e.g., `SubmitButton`)
* Inside the component functions, other “inner” functions can be defined (e.g., `handleSubmit`, typically written in camelCase)
* The component functions return HTML-like code (JSX code)
* Features like `useState()` can be used inside the component functions
* The component functions are exported (via export default)
* Certain features (like `useState` or the custom component `SubmitButton`) are imported via the import keyword.


## Component Functions

Components are functions which is a regular JS construct, not React-specific concept.

When working with React, regular JavaScript functions can be used to encapsulate HTML (or, to be more precise, JSX) code and JavaScript logic that belongs to that markup code.

`handleSubmit` function is also a regular JavaScript function, but it’s not a React component.

```jsx
function calculate(a,b) {
	return {sum: a + b};
}
```
This function doesn't qualify as a React Component. 

>[!important]
>A function will be treated as a component and can therefore be used like an HTML element in JSX code if it returns a renderable value that can be rendered by react (typically JSX code).


>[!note]
>Besides JSX markup, there are a couple of other key values that also qualify as renderable and therefore could be returned by custom components (instead of JSX code). You can also return strings or numbers as well as arrays that hold JSX elements or strings or numbers.



## Rendering the Component

A `root.render(...)` instruction will be in the main entry script of the React project found in the `main.jsx` file, located in the project’s `src/` folder. 

This `render()` method, which is provided by the React library ( react-dom package), takes a snippet of JSX code and interprets and executes it for you.

```jsx
// main.jsx

import React from 'react';
import ReactDOM from 'react-dom/client';

import './index.css';
import App from './App.jsx';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
	<App />
);
```

It may, include an extra `<StrictMode>` element that’s wrapped around `<App>` which turns on extra checks that can help catch subtle bugs in your React code.

The `createRoot()` method instructs React to create a new entry point, which will be used to inject the generated user interface into the actual HTML document that will be served to website visitors.

The argument passed to `createRoot()` therefore is a pointer to a DOM element that can be found in `index.html`, the single page that will be served to website visitors.

All other components are nested in the JSX code of that App component `<App />` or the JSX code of even more nested descendent components.
You can think of all these components building up a tree of components that is evaluated by React and translated into actual DOM-manipulating instructions.

___

### Built-in Components

JSX code is a feature that’s not part of the JavaScript language itself. It’s
basically syntactical sugar (i.e., a simplification regarding the code syntax) provided by the React library and the project setup you’re using to write React code. Therefore, elements like `<div>`, when
used in JSX code, also aren’t normal HTML elements because you don’t write HTML code. It might look like that, but it’s inside a `.jsx` file and it’s not HTML markup. Instead, it’s this special JSX code.

It is important to keep this in mind. Accordingly, these `<div>` and `<h2>` elements you see in all these examples are also just React components in the end. But they are not components built by you, but instead provided by React (or, to be precise, by ReactDOM).

When working with React, you consequently always end up with these primitives—these built-in component functions that are later translated to browser instructions that generate and append or remove normal DOM elements.

### Naming Conventions

You can generally name your React functions however you want—at least in the file where you are defining them. But it is a common convention to use the `PascalCase` naming convention, wherein the first character is uppercase and multiple words are grouped into one single word (`SubmitButton`), where every “subword” then starts with another uppercase character.

In the place where you define your component function, it is only a naming convention, not a hard rule. However, it is a hard rule in the place where you use the component functions, i.e., in the JSX code where you embed your own custom components.
```
<greeting />
```
cannot be used like this. React forces you to use an uppercase starting character for your own custom component names when using them in JSX code.


### JSX as Regular JS Values

JSX elements are just regular JavaScript values (functions, to be precise) in the end. As a result, in a place where only one value is expected (e.g., after the return keyword), you must only have one JSX element

returning two values instead of just one. That is not allowed in JavaScript.

a special kind of wrapping component is used: a React fragment. That’s a built-in component that serves the purpose of allowing you to return or define sibling JSX elements:

This special `<>…</>` element is available in most modern React projects, and you can think of it wrapping your JSX elements with an array behind the scenes.

```jsx
function App() {
	return (
		<>
			<p>Some</p>
			<h1>Heading<h1>
		</>
	);
};
```

The parentheses (()) that are wrapped around the JSX code in all these examples are required to allow for nice multiline formatting. 

In order to split the JSX elements across multiple lines, just as you typically do with regular HTML code in .html files, you need those parentheses; they tell JavaScript where the returned value starts and ends.

Since JSX elements are regular JavaScript values, you can also use JSX elements in all the places where values can be used.
You can also store JSX elements in variables or pass them as arguments to other functions:
```jsx
function App(){
	const content = <p>some</p>;
	 
	return content; 
}
```

## Outputting Dynamic Content

React needs state hook to change the content that is displayed. But there is syntax for outputting dynamic content

```jsx
function App(){
	const = userName = 'Max';

	return <p>Hi, i am {userName}</p>;
};
```

For dynamic content, you use opening and closing curly braces `{…}` with a JavaScript expression (like the name of a variable or constant) between those braces.

You can put any valid JavaScript expression between those curly braces. `{1 + 1}` or `{ getMyName() }`. Anything that produces a single value is allowed in that place.

you can also set dynamic values for attributes:
```jsx
function App() {
	const userName = 'Max';
	return <input type="text" value={userName} />;
};
```

____

### Rendering Images

when working with React, you can use the default <img /> element
* `<img />` must be a self closing tag.
* When displaying local images stored inside of the src/ folder, you must import them into `.jsx` files.

If you store an image in the src/assets folder in a Vite-based React project, and you use that as a path (`<img src="src/assets/my-image.jpg" />`), the image will not load on the deployed website. It will not load there because the deployable folder structure will not contain a src/ assets folder anymore.

Put in other words: You can’t tell the exact path of a locally stored image in advance. That’s why you should import the image file into your .jsx file. As a result, you’ll get a string value that will contain the actual path (which will work in production). This value can then be set as a dynamic value for the src attribute of the `<img />` element:
```jsx
import myImage from './assets/my-image.png';

function App() {
	return <img src={myImage} />;
};
```

if you store an image file (or, actually, any asset) in the `public/` folder of your project, you can directly reference its path.

```jsx
function App() {
	return <img src="/images/demo.jpg" />;
};
```

Which approach should you use then? Store images in src/ or public/?

For most images, src/ is a sensible choice since the pre-processing step assigns a unique file name to each imported file. As a result, files can be cached more efficiently once the application is deployed.

Any files imported in the root index.html file, or files where the file name must never change (e.g., because it’s also referenced by some other app, running on some other server) should typically go into the public/ folder.


## Summary and Key Takeaways

•React embraces components: reusable building blocks that are combined to define the final
user interface
•Components must return renderable content – typically, JSX code that defines the HTML code
that should be produced in the end
•React provides a lot of built-in components: besides special components like <>…</>, you get
components for all standard HTML elements
•To allow React to tell custom components apart from built-in components, custom component
names have to start with capital letters when being used in JSX code (typically, PascalCase
naming is used)
•JSX is neither HTML nor a standard JavaScript feature – instead, it’s syntactical sugar provided
by build workflows that are part of all React projects
•You could replace JSX code with React.createElement(…) calls, but since this leads to signifi-
cantly more unreadable code, it’s typically avoided
•When using JSX elements, you must not have sibling elements in places where single values
are expected (e.g., directly after the return keyword)
•JSX elements must always be self-closing if there is no content between the opening and
closing tags
•Dynamic content can be output via curly braces (e.g., <p>{someText}</p>)
•Images can be rendered by referencing their paths (if stored remotely or in the public/ folder)
or by importing the image files into JSX files and outputting them with the dynamic content
syntax
•In most React projects, you split your UI code across dozens or hundreds of components, which are then exported and imported in order to be combined again

___

