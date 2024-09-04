## Basic Syntax   #02sep24
CSS is made up of various rules, these rules are made up of a 
***selector*** which points to part of HTML and 
***declaration*** which is a ***property : value pair***, a semicolon separated list.
##### Rule : A selector list and an associated declarations block, together, are called a **ruleset**, or often a **rule**.

`<!-- -->`  are comments in HTML 
`/*  */`  are comments in CSS

# Selectors
Selectors refer to the HTML elements to which a particular CSS rules / ***declarations***  applies to;
***selectors*** , are conditions selecting some elements of the page. 

Each (valid) declaration block is preceded by one or more comma-separated selector.

A `<div>` is one of the basic HTML elements. It is an empty container.
In general, it is best to use other tags such as `<h1>` or `<p>` for content but there are many cases where the thing needed is just a container for other elements.

### 1 Universal selector `*`
The universal selector will select elements of any type, hence the name “universal”, and the syntax for it is an asterisk `*`. 
```css
* {
  color: purple;
}
```
Every element would have the `color: purple;` style applied to it.

### 2 Type selectors   `<any tag>`
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

### 3 Class selectors
Class selectors will select all elements with the given class, which is just an attribute you place on an HTML element.

```html
<div class="alert-text">Please agree to our terms.</div>
```
```css
.alert-text {
			  color: red;
			}
```

Syntax for class selectors: 
a period `.` immediately followed by the case-sensitive value of the class attribute. 
Classes aren’t required to be specific to a particular element, so you can use the same class on as many elements as you want.

Another thing you can do with the class attribute is to add multiple classes to a single element as a space-separated list. 
`class="alert-text severe-alert"`.

### 4 ID Selector
ID selectors are similar to class selectors. 
They select an element with the given ID, which is another attribute we place on an HTML element. 
```html
<div id="title">My Awesome 90's Page</div>
```
```css

#title {
		  background-color: red;
		}
```

Syntax for IDs: 
A hashtag `#` immediately followed by the case-sensitive value of the ID attribute. 

The major difference between classes and IDs is that,
an element can have only **one** ID and It cannot be repeated on a single page and should not contain any white space.

A common pitfall is people overusing the ID attribute when they don’t necessarily need to, and when classes will suffice.





Next   [[2 Multiple Selectors]]
