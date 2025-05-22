

# Props in Components


To fully unlock the potential of React components, it would be very useful to configure them just like regular HTML elements. That is possible with
another key React concept called props.

will have some components that are reusable and, therefore, need props and some components that are unique and might not need props.

Two ways of using props in somponents
* Passing props to components
* Consuming props in a component

### Passing props to Components

when working with HTML, you pass content and configuration either between element tags or via attributes. React components work just like HTML elements when it comes to configuring them.

Props are simply passed as attributes (to your component) or as child data between component tags, and you can also mix both approaches:
```jsx
<Product id="abc1" price="12.99" />

<FancyLink target="https://some-website.com">Click me</FancyLink>
```

### Consuming Props in a Component

getting access to the prop values passed into a component, when writing that component’s inner code.

a special parameter value that is passed into every component function automatically by React. This is a special parameter that contains the extra configuration data that is set on the component in JSX code, called the props parameter.

```jsx
<ul>
	<GoalItem id='g1' title='Finish Book' />
	<GoalItem id='g2' title='Learn React' />
</ul>
```

```jsx
function GoalItem(props) {
	return <li>{props.title} (ID: {props.id})</li>;
}
```

The name of the parameter (props) is up to you, but using props as a name is a convention because the overall concept is called props.

props argument will always contain an object (because React passes
an object as a value for this argument), and the properties of this object will be the “attributes” you added to your component (such as the title or id) inside the JSX code where the component is used.

## Special 'children' Prop

React does not just package your attributes into this object; it also adds another extra property to the props object: the special children property (a built-in property whose name is fixed, meaning you can’t change it).

The children property holds a very important piece of data: the content you might have provided between the component’s opening and closing tags.

```jsx
<ul>
	<GoalItem id='g1'>Finish Book</GoalItem>
	<GoalItem id='g2'>Learn React</GoalItem>
</ul>
```

```jsx
function GoalItem(props) {
	return <li>{props.children} (ID: {props.id})</li>;
}
```

You can configure your components with attributes only or use this approach which looks more like the HTML approach.


## Dealing with Multiple Props

You have to add all those props individually (in other words, as separate attributes), or can you pass fewer attributes that contain grouped data. React allows you to pass arrays and objects as prop values as well.

```jsx
<Product title="A book" price={29.99} id="p1" />

// or

const productData = {title: 'A book', price: 29.99, id: 'p1'};

<Product data={productData} />
```

You can use a default JavaScript feature to improve readability: object destructuring instead of doing `props.xyz`.

Object destructuring allows you to extract values from an object and assign those values to variables or constants in a single step:
```js
const user = {name: 'Max', age: 29};

const {name, age} = user; // object destructuring
console.log(name); // outputs 'Max'
```

You can use this syntax to extract all prop values and assign them to equally named variables directly at the start of your component function:

```jsx
function Product( {title, price, id} ) {
	// title, price, id are now available as variables inside this function
}
```

## Spreading Props

you can always accept more and more props (and pass them on to the `<a>` element inside your component), but this reduces the reusability and maintainability of your custom component.

A better solution is to use the standard JavaScript spread operator (i.e., the ... operator) and React’s support for that operator when working with components.

```jsx
function Link({children, config}) {
	return <a {...config} target="_blank" rel="noopener noreferrer">{children}</
	a>;
};
```

config is expected to be a JavaScript object (i.e., a collection of key-value pairs). The spread operator (...), when used in JSX code on a JSX element, converts that object into multiple props.

```js
const config = { href: 'https://some-site.com', download: true };
```

when spreading it on `<a>`, ( `<a {…config}>` ), the result would be the same as if you had written this code:
```
<a href="https://some-site.com" download={true}>
```

___

An alternative, more common pattern uses yet another JavaScript feature: the rest property. That’s a JavaScript pattern that allows you to group properties that have not been destructured into a new object (which then only contains those properties).

```jsx
function Link({children, ...props}) {
	return <a {...props} target="_blank" rel="noopener noreferrer">{children}
	</a>;
};

<Link href="https://google.com">Can you google that for me?</Link>
```

only the children prop is destructured; the other ones are stored in a new object named props. Here, you use the `...` operator in front of the property that should contain all remaining properties.

These behaviors and patterns can be used to build reusable components that should still maintain the configurability of the core element they may be wrapping. This helps you avoid long lists of pre-defined, accepted props and improves the reusability of components.

## Prop Chains / Prop Drilling

A problem every React developer will encounter at some point. It occurs when you build a slightly more complex React app that contains multiple layers of nested components that need to send data to each other.

prop drilling/prop chains is all about: you forward a prop from a component that doesn’t really need it to another component that does need it.

The NavItem component could look like this:
```jsx
function NavItem(props) {
	return <div><AnimatedLink target={props.target} text="Some text" /></div>;
}
```
And AnimatedLink could be defined like this:
```jsx
function AnimatedLink(props) {
	return <a href={props.target}>{props.text}</a>;
}
```
The NavItem component must accept the target prop because it must be passed on to AnimatedLink component.

___

