
### Nesting Elements

you can create a link element like this: This is fine as long as we’re creating just a single element.
```js
const reactLinkElement = React.createElement("a",
	{ href: "http://react.dev" },
	"React Website"
)
```

The solution to creating multi-element structures in a hierarchical manner is nesting elements.

from previous example
```js
const title = React.createElement("h1", null, "Hello world!");

const domElement = document.getElementById("root");

ReactDOM.createRoot(domElement).render(title);
```

`ReactDOM.createRoot().render()` can only take a single `(root)` React element as an argument, which is `reactElement` in this example.

when you use `createElement`, the third argument is the child of the element. In this case, we just supply simple text as the child.

Nesting is the process of organizing nodes in a tree and deciding which nodes will be the children of which other nodes, thus creating the document tree.

___

#### Simple Nesting

Let’s say you want to render the word world in italics in the string “Hello world!” but still put all of it in an h1 element.

```js
const world = React.createElement("em", null, "world");

const title = React.createElement(
	"h1", null, "Hello ", world, "!"
	);
```
we’re passing five arguments to `createElement` now: first, the element type, then the properties, and finally the children of the element.

You can also pass the child elements as an array:
```js
const title = React.createElement("h1", null, ["Hello ", world, "!"])
```

if we already had an array of elements, we could just pass that as an argument by itself.

Putting all this together.
```js
import React from "react";
import ReactDOM from "react-dom/client";

const world = React.createElement("em", null, "world");

const title = React.createElement("h1", null, "Hello ", world, "!");

const domElement = document.getElementById("root");

ReactDOM.createRoot(domElement).render(title);
```

___

### Siblings

In many instances, you can only use a single React element at the top level. This goes for the `ReactDOM.createRoot().render()` method—only a single element can be rendered into the DOM as the root element. 

if you wanted to show a headline and then a link after it, it cant be rendered directly, you have to wrap them in another element.

There are two options, 

One option is to use a neutral DOM element like `<div>`, which is easy, but would add a “physical” element to the output HTML. 

The alternative is to use a React Fragment element `<Fragment>`, which works like any other element, but doesn’t result in any output HTML itself.

```js
import React from "react";
import ReactDOM from "react-dom/client";

const title = React.createElement("h1", null, "Hello world!");
const link = React.createElement("a", { href: "//react.dev" }, "Read more");

const group = React.createElement("div", null, title, link);

const domElement = document.getElementById("root");

ReactDOM.createRoot(domElement).render(group);
```

The `<div>` container is usually a good choice for block-level content, and `<span>` is used for inline-level content. But you don’t have to use a “real” element. 

You can also create an empty React element, whose only purpose is to group multiple other elements and doesn’t output itself into the HTML on the page using `React.Fragment`

```js
import React from "react";
import ReactDOM from "react-dom/client";

const title = React.createElement("h1", null, "Hello world!");
const link = React.createElement("a", { href: "//react.dev" }, "Read more");

const group = React.createElement(React.Fragment, null, title, link); // using Fragment

const domElement = document.getElementById("root");

ReactDOM.createRoot(domElement).render(group);
```

The output of this will be
```js
const group = React.createElement(
	React.Fragment,
	null,
	React.createElement( // title
		"h1",
		null,
		"Hello world!",
	),
	React.createElement( // link
		"a",
		{ href: "//react.dev" },
		"Read more",
	),
);
```


___

for `createElement()` First parameter can have two types of input, as we just saw with the fragments:
* Standard HTML tag as a string, for example, "h1", "div", or "p" (without the angle brackets). The name is in lowercase.
* React component as a reference (not a string). The name is normally capitalized.

___

### Creating Custom Components

There are a lot of elements with a lot of repetition. You need to use the component-based architecture (CBA) which lets you reuse code by separating the functionality into loosely coupled parts.

Component classes, or just components, as they’re often called for brevity.

Think of standard HTML tags as building blocks. You can use them to compose your own React components, which you can use to create custom elements (instances
of components). 

By using custom elements, you can encapsulate and abstract logic in composable, reusable components. This abstraction allows teams to reuse user inter-faces (UIs) in large, complex applications as well as in different projects. Examples include panels, inputs, buttons, menus, and so on.


A custom component is a named object that contains other elements and component instances.

To repeat a link three times, we could create a single Link component that would render the link that we need in the correct way, and then we would include three instances of the Link component rather than the “raw” `<p>` and `<a>` elements with all their properties.

___

You create a React component class by extending the `React.Component` class with `class CHILD extends PARENT` ES6 syntax.

The one mandatory thing you must implement for this new class is the `render()` method. This method must return a single root element created using `createElement()` which is created from another custom component class or an HTML tag. Either can have
nested elements if you so desire as long as there is only one root element.

```js
import React from 'react';
import ReactDOM from 'react-dom/client';

// React Component with Capitalized Name
class Link extends React.Component 
{
	render() // function returning single element
	{
		return React.createElement
		(
			"p",
			null,
			React.createElement
			(
				"a",
				{ href: "//react.dev" },
				"Read more about React"
			)
		);
	}
}

// new instances of Link component
const link1 = React.createElement(Link);
const link2 = React.createElement(Link);
const link3 = React.createElement(Link);

const group = React.createElement(
		React.Fragment,
		null,
		[link1, link2, link3]
);

const domElement = document.getElementById("root");

ReactDOM.createRoot(domElement).render(group);
```

Here`render()` is an expression which returns a single element. (Declarative Coding Style). If you need to return multiple same-level elements, wrap them in a container component—either an HTML element or a
React fragment.

> [!note]
> By convention, the names of variables containing React components are capitalized. This isn’t required in regular JavaScript. But because it’s necessary for JSX we apply this convention here as well.


___

> [!note]
> Components also have properties, life cycle events, states, DOM events, and other features that let you make them interactive and self-contained.

All links are same, you can set element attributes and modify their content and/or behavior individually with properties.

___



