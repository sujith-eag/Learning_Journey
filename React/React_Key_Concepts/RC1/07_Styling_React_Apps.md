
# Styling React App

You can add CSS styles and classes to JSX elements just as you would to regular HTML elements. And in your CSS code, you can use all the features and selectors you know from CSS. There are no React-specific changes you have to make when writing CSS code.

In the root entry file, this is the `main.jsx` file in projects generated via Vite. The import `./index.css`; statement leads to the CSS file being imported and the defined CSS code
being applied to the rendered web page.

during the transpilation process, the transpiler identifies the CSS import, removes it from the JavaScript file, and injects the CSS code (or an appropriate link to the potentially bundled and optimized CSS file) into the index.html file.

### using Inline Styles

Even though it’s typically discouraged, you can also set inline styles directly on JSX elements via the style prop.

```jsx
function TodoItem() {
	return <li style={{color: 'red', fontSize: '18px'}}>Learn React!</li>;
};
```

This approach differs from what you would use to set inline styles when working with just HTML
```html
<li style="color: red; font-size: 18px">Learn React!</li>
```

The difference is that the style prop expects to receive a JavaScript object that contains the style settings—not a plain string.

Since the style object is an object and not a plain string, it is passed as a value between curly braces, just as an array, a number, or any other non-string value would have to be set between curly braces (anything between double or single quotes is treated as a string value).

uses one pair of curly braces to surround the non-string value and another pair to surround the object data.

When setting styles in JavaScript code (as with the style prop shown above), JavaScript CSS property names have to be used. Those names are similar to the CSS property names you would use in CSS. Differences occur for property names that consist of multiple words. When targeting such properties in JavaScript, camelCase notation must be used (fontSize instead of font-size), as JavaScript properties cannot contain dashes. Alternatively, you could wrap the property name with quotes ('font-size').

### Setting Styles via CSS Classes

Should not add class as a prop and, instead, use className since class is a keyword in javscript.

```jsx
<ul>
	<li className="goal-item">Learn React!</li>
	<li className="goal-item">Master React!</li>
</ul>
```

```css
.goal-item {
	color: red;
	font-size: 18px;
}
```

### Setting Styles Dynamically

Based on user entry using state and inline style
```jsx
function coloredText() {
	const [enteredColor, setEnteredColor] = useState('');
	
	function handleTextColor(event){
		setEnteredColor(event.target.value);
	}
	
	return(
		<>
			<input type='text' onChange={handleTextColor} />
			<p style={ {color:eneredColor} }>
				This text is Dynamically colored
			</p>
		</>
	);
}
```

Applying style by altering the class name with optional state selection.

```jsx
function TodoPriority() 
{
	const [chosenPriority, setChosenPriority] = useState('low-prio');

	function handleChoosePriority(event) 
	{
		setChosenPriority(event.target.value);
	};
	
	return (
		<>
			<p className={chosenPriority}>Chosen Priority: {chosenPriority}</p>
			<select onChange={handleChoosePriority}>
				<option value="low-prio">Low</option>
				<option value="high-prio">High</option>
			</select>
		</>
	);
};
```

```css
.low-prio {
	background-color: blue;
	color: white;
}
.high-prio {
	background-color: red;
	color: white;
}
```

### Conditional Styles

Choosing based on Conditional and Boolean passed

```jsx
function TexrInput({isValid, isRecommended, ...props}){
	let cssClass = 'input-default';
	
	if(isRecommended){
		cssClass = 'input-recommended';	
	}
	
	if(!isValid){
		css = 'input-invalid'
	}

	return(
		<input className={cssClass} {...props} />
	);
}
```

The main purpose of this wrapper component is to set some default styles for the wrapped `<input>` element. The wrapper component is built to provide a pre-styled input element that can be used anywhere in the app.

Similarly using inline styling
```jsx
function TextInput({isValid, isRecommended, ...props}) {
	let bgColor = 'black';
	
	if (isRecommended) 
	{
		bgColor = 'blue';
	}
	
	if (!isValid) 
	{
		bgColor = 'red';
	}
	
	return <input style={{backgroundColor: bgColor}} {...props} />
};
```

### Combining Multiple Dynamic CSS Classes

```jsx
function ExplanationText({children, isImportant}) {
	const defaultClasses = 'text-default text-expl';
	
	return <p className={defaultClasses}>{children}</p>;
}
```

Or using a String directly bu adding another class is difficult
```jsx
return <p className="text-default text-expl">{children}</p>;
```

Conditional Assignment
```jsx
function ExplanationText({children, isImportant}) {
	let cssClasses = 'text-default text-expl';

	if (isImportant) {
		cssClasses = 'text-important';
	}
	
	return <p className={cssClasses}>{children}</p>;
}
```

* String concatenation:
```jsx
cssClasses = cssClasses + ' text-important';
```

* Using a template literal:
```jsx
cssClasses = `${cssClasses} text-important`;
```

* Joining an array:
```jsx
cssClasses = [cssClasses, 'text-important'].join(' ');
```

These examples could all be used inside the if statement (if (isImportant)) to conditionally add the text-important class.
Any approach that yields a string can be used to generate values for className.


### Merging multiple inline style Objects

The main difference is that you don’t produce a string with all values but, rather, an object with all combined style values.

```jsx
function ExplanationText({children, isImportant}) {
	let defaultStyle = { color: 'black' };

	if (isImportant) {
		defaultStyle = { ...defaultStyle, backgroundColor: 'red' };
	}
	
	return <p style={defaultStyle}>{children}</p>;
}
```

## Components with Customizable Styles

The same component can be used in different places on a page with different configurations to yield a different output.

```jsx
function Button({children, config, className}) {
	return <button {...config} className={`btn ${className}`}>{children}</but-
ton>;
};

```

This component could be used in another component in the following way. The final `<button>` element would receive both the btn as well as btn-alert classes.
```jsx
<Button config={{onClick: doSomething}} className="btn-alert">Click me!</But-
ton>
```

Overriding the className instead of merging with default.

```jsx
function Button({children, config, className}) {
	let cssClasses = 'btn';

	if (className) {
		cssClasses = className;
	}
	
	return <button {...config} className={cssClasses}>{children}</button>;
};
```

## Customization with Fixed Configuration Options

```jsx
function App() {
	return(
		<>
			<TextBox mode='info'>
				Visit React.dev for API References
			</TextBox>
			
			<TextBox mode='alert'>
				Loading failed
			</TextBox>
		</>
	);
}
```

```jsx
function TextBox({children, mode}) {
	let cssClasses;
	
	if(mode === 'alert') {
		cssClasses='box-alert';
	} else if (mode === 'info') {
		cssClasses='box-info';
	}
	
	return(
		<p className={cssClassname}>{children}</p>;
	);
}
```

The styling is not set with class name but with help of specific prop.



## Problem with Unscoped Styles

Some styles are relevant to specific components only, not all of them. If any other had the same className there would be conflict because they are not scoped(restricted) to specific component.

>[!note]
>CSS Styles are global unless inline style is used


Various solutions for this problem have been developed, the following are three of the most popular solutions:
* CSS Modules (supported out of the box in React projects created with Vite)
* Styled components (using a third-party library called styled-components)
* Tailwind CSS (a popular CSS library)


### Scoped Styles with CSS Modules

CSS Modules is the name for an approach where individual CSS files are linked to specific JavaScript files and the components defined in those files. 

This link is established by transforming CSS class names, such that every JavaScript file receives its own, unique CSS class names. This transformation is performed automatically as part of the code build workflow.

CSS Modules are enabled and used by naming CSS files in a very specific and clearly defined way: `<anything>.module.css`, `TextBox.module.css`. 

The `.module` part in front of the file extension is required, as it signals (to the project build workflow) that this CSS file should be
transformed according to the CSS Modules approach.

___

When importing the normal `import './index.css'` the CSS code is simply merged into the `index.html` file and applied globally.

When using CSS Modules instead, the CSS class names defined in the imported CSS file are transformed such that they are unique for the JS file that imports the CSS file.

```jsx
import classes from './file.module.css';

import classes from './TextBox.module.css';
```

___

```css
<!- TextBox.module.css --> 

.alert {
	padding: 1rem;
	border-radius: 6px;
	background-color: #f9bcb5;
	color: #480c0c;
}
.info {
	padding: 1rem;
	border-radius: 6px;
	background-color: #d6aafa;
	color: #410474;
}
```

```jsx
// TextBox.jsx

import classes from './TextBox.module.css';

function TextBox({ children, mode }) {
	let cssClasses;
	
	if (mode === 'alert') 
	{
		cssClasses = classes.alert;
	} 
	else if (mode === 'info') 
	{
		cssClasses = classes.info;
	}

	return <p className={cssClasses}>{children}</p>;
}

export default TextBox;
```

The final class name code will not match the set class names

```jsx

<p class='_info_1mtzh_8'>CSS Module Can be Useful</p>
```


If any other CSS file, imported by another JavaScript file, were to define a class with the same name, the styles would not clash and not overwrite each other.

>[!important]
>You can only use CSS class selectors because CSS Modules rely on CSS classes. You can't add selectors that don't use classes at all like `input{}` `#some-id{}`


You can write selectors that combine classes with other selectors, such as `input.invalid {}`

### Styled-components Library

It is a CSS-in-JS solution which aims to remove the separation between CSS code and the JS code by merging them into the same file.

>[!note]
>styled-components is a third-party library that’s not pre-installed, you have to install this library as a first step if you want to use it. `npm install styled-components`

The styled-components library essentially provides wrapper components around all built-in core components (as in, around p, a, button, input). 

It exposes all these wrapper components as tagged templates JavaScript functions that aren’t called like regular functions but, instead, are executed by adding backticks (a template literal) right after the function name. 

```
doSomething`text data`
```

```jsx
import styled from 'styled-components';

const Button = styled.button`
	background-color: #370566;
	color: white;
	border: none;
	padding: 1rem;
	border-radius: 4px;
`;

export default Button;
```

```jsx
import Button from './components/button.jsx';

function App() {
	function handleClick() {
		console.log('This button was clicked!');
	}
	
	return <Button onClick={handleClick}>Click me!</Button>;
}

export default App;
```

### Using Tailwaind CSS Library for Styling

Tailwind has become a very popular styling solution for React projects (for developers who don’t want to write custom CSS code).

```jsx
function App() {
	return (
		<main
className="bg-gray-200 text-gray-900 h-screen p-12 text-center">
			<h1 className="font-bold text-4xl">Tailwind CSS is amazing!</h1>
			<p className="text-gray-600">
				It may take a while to get used to it. But it's great for people who don't want to write custom CSS code.
			</p>
		</main>
	);
}

export default App;
```


Tailwind’s approach offers many advantages:

* You don’t need to learn CSS in detail—understanding the Tailwind syntax, which is less complex than writing CSS from scratch, suffices.
* You compose styles by combining CSS classes—similar to how you compose user interfaces from components in React.
* You don’t have to switch between JSX and CSS files.
* Styling changes can be applied and tested very quickly.

`https://tailwindcss.com/docs/utility-first`



here are other kinds of CSS and JavaScript libraries, too:
* Utility libraries that solve very specific CSS problems—independent of the fact that you’re using them in a React project (for example, Animate.css, which helps to add animations)
* Other CSS frameworks or libraries that provide a broad variety of pre-built CSS classes that can be applied to elements to quickly achieve a certain look (for example, Bootstrap)
* JavaScript libraries that help with styling or specific styling aspects like animations (for example, Framer Motion)


____




