
```jsx
import { useState } from 'react';

function TermsOfUse(){
	const [showTerm, setShowTerm] = useState(false);
	
	function handleShowTerms() {
		setShowTerms(true);
	}
	
	let paragraph;
	
	if(showTerms) {
		paragraph = <p>By continuing you accept the conditions</p>;
	}
	
	return(
		<section>
			<button onClick={handleShowTerms}>
				Show Terms of Use Summary
			</button>
			{paragraph}
		</section>
	);
} 
```


If `showTerms` is false, paragraph stores the value undefined
and nothing is rendered to the DOM. Therefore, inserting null or undefined in JSX code leads to nothing being outputted by React. But if `showTerms` is true, the complete paragraph is saved as a value and outputted in the DOM.


>[!tip]
>You could store entire JSX tree structures (such as multiple, nested, or sibling JSX elements) inside variables or constants. As a simple rule, anything that can be returned by a component function can be stored in a variable.

___

Alternatively, you could also do the following:
* Utilize ternary expressions.
* Abuse JavaScript logical operators.
* Use any other valid JavaScript way of selecting values conditionally.


#### Utilizing Ternary Expressions

```js
let a = 1;
if (someCondition) {
	a = 2;
}


const a = someCondition ? 2 : 1;
```

Using in the previous Example

```jsx
import { useState } from 'react';

function TermsOfUse(){
	const [showTerm, setShowTerm] = useState(false);
	
	function handleShowTerms() {
		setShowTerms(true);
	}
	
	const paragraph = showTerms ? <p>By continuing you accept the conditions</p> : null;
	}
	
	return(
		<section>
			<button onClick={handleShowTerms}>
				Show Terms of Use Summary
			</button>
			{paragraph}
		</section>
	);
} 
```

Using it inline by utilizing the ternary expression directly inside of the JSX snippet.

```jsx
import { useState } from 'react';

function TermsOfUse(){
	const [showTerm, setShowTerm] = useState(false);
	
	function handleShowTerms() {
		setShowTerms(true);
	}
	
	return(
		<section>
			<button onClick={handleShowTerms}>
				Show Terms of Use Summary
			</button>
			{showTerms ? <p>By continuing you accept the conditions</p> : null}
		</section>
	);
} 
```



#### Abusing JavaScript Logical Operators


```jsx
<div>
	{showDetails ? <h1>Product Details</h1> : null}
</div>
```
The null can be avoided by using Logical operators
```jsx
<div>
	{showDetails && <h1>Product Details</h1>}
</div>
```


In JavaScript, the && operator returns the second value (that is, the value after &&) if the first value is true or truthy (that is, not false, undefined, null, 0, and so on). 

&& operator is used in if statements or ternary expressions, but when working with React and JSX, you can take advantage of the behavior described previously to output truthy values conditionally. This technique is also called short-circuiting.

```js
console.log(1 === 1 && 'Hello');
```

```jsx
const languages = {
	de: 'de-DE',
	us: 'en-US',
	uk: 'en-GB'
};

function LanguageSelector( {country} ) {
	return <p>Selected Language: {language[country]}</p>;
}
```

Selecting property values dynamically like this is another common pattern for picking values from a map of values. It is therefore an alternative to specifying multiple if statements or ternary expressions.

#### Setting Element Tags Conditionally

```jsx
function Button({isButton, config, children}) {
	if(isButton) {
		return( <button {...config}>{children}</button>);
	}
	return( <a {...config}>{children}</a>);
};
```
This Button component checks whether the isButton prop value is truthy and, if that is the case, returns a `<button>` element.

```jsx
function Button({isButton, config, children}) {
	const Tag = isButton ? 'button' : 'a';
	return <Tag {...config}>{children}</Tag>;
};
```

The special behavior is that tag names can be stored (as string values) in variables or constants, and that those variables or constants can then be used like JSX elements in JSX code (as long as the variable or constant name starts with an uppercase character, like all your custom components).

___

The same pattern could also be used with custom components. Instead of storing string values, you would store pointers to your custom component functions through the following:
```jsx
import MyComponent from './my-component.jsx';
import MyOtherComponent from './my-other-component.jsx';

const Tag = someCondition ? MyComponent : MyOtherComponent;
```

____