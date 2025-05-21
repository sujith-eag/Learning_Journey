

#### Working with properties

Think of properties as unchangeable values within an element. They allow elements to have different
variations if used in a view, such as changing a link URL by passing a new value for a property

`React.createElement("a", { href: "//react.dev" }, "React");`

properties are immutable within their components. A parent assigns properties to its children upon their creation. The child element isn't supposed to modify its properties.

Properties closely resemble HTML attributes (like `href, title, style, class`), this is one of their purpose, but they have another, to create custom instructions for components to make them render individually.


The object of properties can be accessed inside a component using this.props. This object is a frozen (immutable) object, from which you can only read values, not set them.

Just know that you should never try to edit or add properties inside a component itself. That is something you do in the parent context.


___

#### A single property

If we want the name of out links to be customized, we need to:
* Pass a property to our component instances.
* Use the property inside the component.

Rather than just using, 
`const link1 = React.createElement(Link);`

we'll supply an object as second argument with a single property:
`const link1 = React.createElement(Link, {framework: "React" });`

We used the variable name `framework` here. We now need to use this passed property inside our class.

Given that we called the variable framework, we’ll access it through `this.props.framework`.

___

```js
import React from 'react';
import ReactDOM from 'react-dom/client';

class Link extends Component
{
	render()
	{
		return React.createElement
		(
			"p",
			null,
			React.createElement
			(
				"a",
				{ href: "//react.dev" },
				`Read more about ${this.props.framework}`,
			),
		);
	}
}

const link1 = React.createElement( Link, 
		{ framework: "React" });
		
const link2 = React.createElement( Link, 
		{ framework: "Vue" });
		
const link3 = React.createElement( Link, 
		{ framework: "Angular" });

const group = React.createElement
(
	React.Fragment,
	null,
	link1, link2, link3
);

const domElement = document.getElementById("root");

ReactDOM.createRoot(domElement).render(group);
```

`Read more about ${this.props.framework}`, is used to render the text content of link by combining static text with `this.props.framework`.

___

#### Multiple Properties

All the links still point to the same URL, which is the React website. because we need the URLs to be different. Using the same approach, we simply invent a new property, `url`, and use it inside the component as well as in the component instances.

```js
import React from 'react';
import ReactDOM from 'react-dom/client';

class Link extends Component
{
	render()
	{
		const link = React.createElement
		(
			"a",
			{ href: this.props.url },
			`Read more about ${this.props.framework}`
		);
		return React.createElement
		(
			"p",
			null,
			link
		);
	}
}

const link1 = React.createElement( Link, 
		{ framework: "React", url: "//react.dev" });
		
const link2 = React.createElement( Link, 
		{ framework: "Vue", url: "//vuejs.org", });
		
const link3 = React.createElement( Link, 
		{ framework: "Angular", url: "//angular.io", });

const group = React.createElement
(
	React.Fragment,
	null,
	link1, link2, link3
);

const domElement = document.getElementById("root");

ReactDOM.createRoot(domElement).render(group);
```

What happens if you mess up and set a custom property on an HTML element? React will render it anyway.

___

You can completely modify the rendered elements based on the value of a property. For example, we can examine the framework property and return a huge title
with a link in case the framework name is "React":

```js
class Link extends Component
{
	render()
	{
		const link = React.createElement
		(
			"a",
			{ href: this.props.url },
			`Read about ${this.props.framework}`,
		);
		if (this.props.framework == "React")
		{
			return React.createElement
			(
				"h1",
				null,
				link
			);
		}
		return React.createElement
		(
			"p",
			null,
			link
		);
	}
}
```

This is also a great example of React elements being just plain old JavaScript. We can create an element and store it in a variable, and then later use that variable as we see
fit.

We can also create branching using regular JavaScript functionality.

It’s very important to know how React works in regular JavaScript if you plan to use JSX. This is because, in the end, browsers will still run regular JavaScript, and you’ll need to understand the results of the JSX-to-JS transpiling from time to time.

___
