### Overview  #02sep24
Add styles to HTML with CSS
Using class and ID attributes
Adding style to specific elements using the correct selectors

## Basic Syntax
CSS is made up of various rules
These rules are made up of a ***selector***
and ***declaration*** which is a ***property : value pair***, a semicolon separated list.

#### Declaration
- The **property** which is an identifier, that is a human-readable _name_, that defines which feature is considered.

- The **value** which describe how the feature must be handled by the engine. Each property has a set of valid values, defined by a formal grammar, as well as a semantic meaning, implemented by the browser engine.

```CSS
div.bold-text { font-weight: 700; }
    selector    property     value
```

Declarations are grouped in blocks, which is delimited by `{  }`. Such blocks are called declaration blocks.
Separate declarations are separated by a `;`
Blocks can be nested sometimes but braces must be matched.

```css
{
	A CSS block
}
```

## Selectors
Selectors refer to the HTML elements to which CSS rules apply; 
they’re what is actually being “selected” for each rule.

Selectors are used to apply different ***declarations*** to different parts of the document. CSS allows this by associating conditions with declarations blocks. 

Each (valid) declaration block is preceded by one or more comma-separated **selectors**, which are conditions selecting some elements of the page. 

#### Rule
A selector list and an associated declarations block, together, are called a **ruleset**, or often a **rule**.




A `<div>` is one of the basic HTML elements. It is an empty container.
Many of our exercises use plain`<div>`s for simplicity.

In general, it is best to use other tags such as `<h1>` or `<p>` for content but there are many cases where the thing needed is just a container for other elements.






### Universal selector
The universal selector will select elements of any type, hence the name “universal”, and the syntax for it is a simple asterisk `*`. 
In the example below, every element would have the `color: purple;` style applied to it.

```css
* {
  color: purple;
}
```

### Type selectors
A type selector (or element selector) will select all elements of the given element type, and the syntax is just the name of the element:

```html
<!-- index.html -->

<div>Hello, World!</div>
<div>Hello again!</div>
<p>Hi...</p>
<div>Okay, bye.</div>
```
```css
/* styles.css */

div {
  color: white;
}
```
Here, all three `<div>` elements would be selected, while the `<p>` element wouldn’t be.

### Class selectors
Class selectors will select all elements with the given class, which is just an attribute you place on an HTML element. 

```html
<div class="alert-text">Please agree to our terms of service.</div>
```
```css
.alert-text {
  color: red;
}
```
Syntax for class selectors: a period immediately followed by the case-sensitive value of the class attribute. Classes aren’t required to be specific to a particular element, so you can use the same class on as many elements as you want.

Another thing you can do with the class attribute is to add multiple classes to a single element as a space-separated list, such as `class="alert-text severe-alert"`.

## ID Selector
ID selectors are similar to class selectors. 
They select an element with the given ID, which is another attribute you place on an HTML element. 

The major difference between classes and IDs is that an element can only have **one** ID. It cannot be repeated on a single page and should not contain any white space

```html
<div id="title">My Awesome 90's Page</div>
```
```css

#title {
  background-color: red;
}
```

For IDs, instead of a period, we use a hashtag immediately followed by the case-sensitive value of the ID attribute. 

A common pitfall is people overusing the ID attribute when they don’t necessarily need to, and when classes will suffice.
