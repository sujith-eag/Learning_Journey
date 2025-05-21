
### Introduction to JSX

JavaScript XML (JSX) is a syntax extension to JavaScript. It’s one of the things that make React great, but it was also one of the more controversial elements of React.

`const link = <a href="//react.dev">React</a>;`

JSX is the element that appears between the angle brackets, it is not a string, not a template literal and not HTML.

It is a JavaScript Object that created with the syntax extension called JSX.
It makes creating React elements much faster and more compact and makes reading React elements much easier.

JSX is made for developers only, it doesn't do anything to make better or faster web applications. JSX is converted to the same code you get when not
using JSX.

___

JSX is a JavaScript extension that provides syntactic sugar i.e., making it easier to type. for function calls and object construction, particularly a replacement for `React.createElement()`

JSX produces React elements while allowing you to harness the full power of JavaScript.
* Easier to read, better developer experience
* Better error messages
* Fast code
* Fewer syntax error, less code to type.

___


Without JSX
```js
const element = React.createElement
(
	'main',
	null,
	React.createElement(Title, null, 'Welcome'),
	React.createElement(Carousel, {images: 6}),
	React.createElement('a', {href: "/blog"}, 'Go to the blog'),
);
```

```jsx
const element = <main>
	<Title>Welcome</Title>
	<Carousel images={6} />
	<a href="/blog">Go to the blog</a>
</main>;
```
It looks like HTML, which is very easy to read, and it’s partially identical to the HTML output that will be rendered, except for the custom components.


___

Keeping HTML and JS together

In essence, JSX is a small language with an XML-like syntax. JSX isn’t valid JavaScript on its own and
can’t be compiled directly by a JavaScript compiler. It has to be transpiled first.

Instead of writing `React.createElement(NAME, ...)`. function call over and over, you can instead use `<NAME />`.


___

### Understanding JSX

With create-react-app (CRA), you get JSX transpiling “for free,” so you don’t have to worry about setting it up yourself.


#### Creating elements with JSX

```jsx
React.createElement('h1')

<h1 />
```

```jsx
React.createElement(
	'h1',
	null,
	'Welcome',
	);

<h1> 
	Welcome
</h1>
```

```jsx
React.createElement(
	Title,
	null,
	'Welcome',
	);

<Title> 
	Welcome
</Title>
```

```jsx
React.createElement(
	Title,
	{ size: 6 }
	'Welcome',
	);

<Title size="6"> 
	Welcome
</Title>
```

```jsx
React.createElement(
	Title,
	{ size: 6 }
	'Welcome to ',
	React.createElement(
		'strong',
		null,
		'Narnia'
	),
	);

<Title size="6"> 
	Welcome to
	<strong>Narnia</strong>
</Title>
```

___

```js
import React, { Component } from 'react';

class App extends Component 
{
	render() 
	{
		return React.createElement
		(
			'h1',
			null,
			'Hello ',
			React.createElement('em', null, 'world'),
			'!',
		);
	}
}
export default App;
```

```jsx
import React, { Component } from 'react';

class App extends Component 
{
	render() 
	{
		return <h1>Hello <em>World</em>!</h1>;
	}
}

export default App;
```

You can even store objects created with JSX syntax in variables because JSX is just a syntactic improvement of `React.createElement()`.

```jsx
const title = <h1>Hello <em>World</em>!</h1>;
return title;
```

___

#### Using JSX with custom components

The previous example used the `<h1>` JSX tag, which is also a standard HTML tag name.
When working with custom components, you apply the same syntax. The only difference is that the component class name must start with a capital letter, as in `<Title />`.

The link example in JSX
```jsx
import { component, Fragment } from 'react';

class Link extends Component
{
	render()
	{
		return
		(
			<p>
			<a href="//react.dev">Read more anout Ract</a>
			</p>
		);
	}
}

class App extends Component
{
	render()
	{
		return 
		(  // parenthesis starts returned JSX
			<Fragment>
				<Link />
				<Link />
				<Link />
			</Fragment>
		);
	}
}
```

___

#### Multiline JSX objects

Parentheses around the returned multiline JSX object, these parentheses are needed if you start a multiline JSX object on a separate line after, for example, a return.

```jsx
return (
	<main>
		<h1>Hello world</h1>
	</main>
);
```

Alternatively, you can start your root element on the same line as return and avoid the parentheses.

```jsx
return <main>
	<h1>Hello world</h1>
</main>;
```

exact same thing goes for any other use of multiline JSX objects, for example, when you save them in a variable.
```jsx
const message = (
	<main>
		<h1>Hello world</h1>
	</main>
);
```


___

#### Outputting variables in JSX

It would be useful if a date component uses the current date and time, and not just a hardcoded value.
When working with JavaScript-only React, you have to use string template literals (i.e., backticks) to mix strings with variables.

```js
class DateTimeNow extends React.Component
{
	render()
	{
		const dateTime = new Date().toLocaleString();
		
		return React.createElement
		(
			'span',
			null,
			`Current date and time is ${dateTime}.`
		);
	}
}
```

In JSX, you can use curly brace `{}` notation to output variables dynamically, which reduces code complexity.
```jsx
class DateTimeNow extends React.Component
{
	render()
	{
		const dateTime = new Date().toLocaleString();
		
		return <span>Current date and time is {dateTime}.</span>
	}
}
```

___

If you reference a variable that is a React element (optionally created using JSX), you can directly insert that other bit of JSX in current context.

```jsx
const now = <date>{dateTimeNow}</date>;
const message = <p>Today is {now}</p>;

// Equivalent to directly inserting the element:
const message = <p>Today is <date>{dateTimeNow}</date></p>;

// Variables can also be properties
<p>Hello {this.props.userName}, today is {dateTimeNow}.</p>
```

___

You can also invoke methods of your component that you create yourself. That is a common practice to isolate bits of functionality

```jsx
import {component } from 'react';

class ButtonList extends Component
{
	getButton(text)
	{
		return(
			<button disabled ={this.props.disabled}>
			{text}
			</button>
		);
	}
	
	render()
	{
		return(
			<aside>
				{this.getButton('Up')}
				{this.getButton('Down')}
			</aside>
		);
	}
}
```

`getButton()` method takes text argument to be label of button. It also depends on passed property to component.

The purpose of this example is to show that you can invoke component methods directly in JSX.

you can execute arbitrary JavaScript expressions inside the curly braces, such as formatting a date directly.

```jsx
<p>Today is 
	{new Date(Date.now()).toLocaleTimeString()}.</p>
```

```jsx
import { Comonent } from 'react';

class App extends Component
{
	render()
	{
		const world = <em>World</em>;
		return <h1>Hello {world}!</h1>;
	}
}
export default App;
```

___

#### Working with properties in JSX

Element properties are defined using attribute syntax. That is, you use `key1=value1 key2=value2…` notation inside the JSX tag to define both HTML attributes and React component properties. This is similar to attribute syntax in HTML/XML.

```jsx
return <a href="//react.dev">Let's do React!</a>;

// on custom Link component
return <Link url=”//react.dev” framework=”React” />;
```

Using hardcoded values for attributes isn’t all that flexible, of course. If you want to reuse the Link component, then the href must change to reflect a different address each time. This is called dynamically setting values versus hardcoding them.

A dynamic component `ProfileLink` that renders a link with properties `url` and `label` for `href` and `title`, respectively.

```jsx
class ProfileLink extends React.Component 
{
	render()
	{
		return(
			<a
				href={this.props.url}
				title={this.props.label}
				target="_blank" 
				>Profile</a>
		);
	}
}

<ProfileLink url="/users/johnny" label="Profile for Johnny" />
```

___

if you have an object with values, and you want to render all of them, you can do so using the spread operator as follows:
```jsx
return <Post {...post} />;
```
Note that this will render every property of the post object, regardless of whether that makes sense or not.

If you have an object with properties that you want to render on an element, you
can render each of them one by one as follows:
```jsx
return (
	<Post
		id={post.id}
		title={post.title}
		content={post.content}
	/>
);
```
This works great and is a safe solution.

___

#### THE SPECIAL PROPERTY: CHILDREN

Link list with child nodes in JSX

```jsx
import { Fragment, Component } from "react";

class Link extends Component 
{
	render()
	{
		return(
			<p>
				<a href={this.props.url}>
					{this.props.children}
				</a>
			</p>
		);
	}
}

class App extends Component
{
	render()
	{
		return(
			<Fragment>
				<Link url="//react.dev">
					<strong>React</strong>
				</Link>
				
				<Link url="//vuejs.org">
					Vue
				</Link>
				
				<Link url="//angular.io">
					Angular
				</Link>
			</Fragment>
		);
	}
}
export default App;
```


If we could have passed the content for Link as a property, but it would have looked pretty bad. 

```jsx
<p>
	<a href={this.props.url}>
		{this.props.content}
	</a>
</p>


<Link
	url="//react.dev"
	content={<strong>React</strong>}
/>
```

But when we use the children approach, it becomes
```jsx
<p>
	<a href={this.props.url}>
		{this.props.children}
	</a>
</p>


<Link url="//react.dev">
	<strong>React</strong>
</Link>
```

___

