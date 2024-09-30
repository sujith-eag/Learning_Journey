Manipulating DOM with `js`
# Document Object Model

The browser builds up a model of the HTML document's structure and uses this model to draw the page on the screen. This representation of the document's structure that can be read or modified. 
It is a live data structure: when it's modified, the page on the screen is updated to reflect the changes.

HTML is a set of boxes, For each box there is an object we can interact with to find out things such as what HTML tag it represents and which boxes and text it contains.
This representation is DOM.

DOM is tree like representation of contents of a webpage - a tree of "nodes" of different relationships depending on how they are arranged in the HTML document.

"element" nodes are primarily used for manipulating the DOM
```html
<div id = "container">
	<div class = "display"> </div>
	<div class = "controls"> </div>	
</div>
```
Here there is a parent and its children which are on the next level, each on their own branch.


## Targeting nodes with selectors

When working with DOM, 'selectors' are used to target the nodes to be worked on.
Using CSS style selectors to target the `<div class = "display"> </div>`:
```css
.display
div.display
#container > .display
div#container > div.display
```

Using relational selectors (i.e `firstElementChild` or `lastElementChild`) with special properties owned by the nodes.
Identifying a certain node based on its relationship to the nodes around it. 
```js
// selects the #container div
const container = document.querySelector("#container");

// selects the first child of #container  i.e .display
console.dir(container.firstElementChild);

// selects the .controls div
const controls = document.querrySelector(".controls");

// selects the prior sibling of control i.e .display
console.dir(controls.previousElementSibling);
```


## DOM Methods

When a HTML file is parsed into DOM, the nodes will be JavaScript objects that have properties and methods attached to them.
These are the primary tools we are going to use to manipulate our webpage with `js`




***Basic DOM Manipulation***

To manipulate an element inside the DOM, first it needs to be selected and store a reference to it in a variable.  `const link = document.querySelector("a");`
Query Selector is standard way because it allows CSS style selection of elements.

This stored reference can be manipulated using properties and methods available to it.
`link.textContent = "Adding text to the anchor tag";`
`link.href = "https://developer.mozilla.org";`



#### Query selectors

```js
element.querySelector(selector) 
// returns a reference to the first match of 'selector'

element.querySelectorAll(selectors) 
// returns 'NodeList' containing references to all matches of the 'selector'
```
`NodeList` is not an Array even though it looks like an array it has several array methods missing from it.  It can be converted to an Array using `Array.from()` or [spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

#### Element creation

```js
document.createElement(tagName, [options])

const div = document.createElement("div")
```
Creates a new element of `tagName` tag type.
`[options]` to add some optional parameters to the function.

This function does not put the new element into the DOM - it creates it in memory.
It can be manipulated by adding style, classes, ids, text, etc before placing it on the page.

#### Append elements

The element can be placed in DOM with one of these.
```js
parentNode.appendChild(childNode)
// appends childNode as last child of parentNode

parentNode.insertBefore(newNode, referenceNode)
// inserts newNode into parentNode before referenceNode
```

Remove element
```js
parentNode.removeChild(child)
// removes child from parentNode and returns a reference to child.
```



#### Altering Elements Style

When there is a reference to an element, it can be used to alter the properties, attributes, class and styling of that element.

```js
// create a new div element
const div = document.createElement("div");

// adding inline styling

// add indicated style rule to the element in the div variable
div.style.color = 'blue';
```

```js
// add several style rules
div.style.cssText = "color: blue; background: white;";
```

```js
// adds several style rules using Element.setAttributes()

div.setAttribute("style", "color: blue; background: white;");
// this takes two arguments, the attribute you want to set and the value.

div.setAttribute("class", "highlight");
// setting a class name of highlight
```

When accessing kebab-cased CSS property like `background-colour` with `js`,
With dot notation, camelCase can be used.
With bracket notation, both camelCase and kebab-case can be used but the property name must be a string.
```js
// this will not work as it tries to substract
div.style.background-color;

div.style.backgroundColor;
// dot notion with camelCase works

// bracket notaion with kebab-case works
div.style["background-color"];

div.style["backgroundColor"];
// bracket notation with camelCase also works
```
```js
div.style.padding = "10px";
div.style.backgroundColor = "red";
div.style.textAllign = "center";
div.style.width = "250px";
```

#### Editing attributes

```js
div.setAttribute("id", "theDiv");
// if id exists, update it to 'theDiv', else create an id with value 'theDiv'

div.getAttribute("id");
// returns value of specified attrbute, in this case "theDiv"

div.removeAttribute("id");
// removes specified attribute
```

[HTML attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes) to check out????


#### Working with classes

```js
div.classList.add("new");
// adds class 'new' to the new div

div.xlassList.remove("new");
// removes 'new' class from div

div.classList.toggle("active");
// if div doesn't have class 'active' then add it, if it does, then remove it.
```
It is often standard and cleaner to toggle CSS style rather than adding and removing inline CSS. 


#### Adding text content and HTML content
```js
div.textContent = "Hello World!";
// creates a text node containing "hello world" and inserts it in div

div.innerHTML = "<span>Hello World!</span>";
// renders the HTML inside div
```
It is preferred to using text content over inner html for adding text to avoid security risks.


____
___


## Demo of stuff

```html
<!-- HTML file -->

<body>
	<h1>TITLE OF WEBPAGE</h1>
	<div id="container"></div>
</body>
```

```js
// JavaScript file

const container = document.querrySelector("#container");

const content = document.createElement("div");  // make a div
content.classList.add("content");     // add a class
content.textContent = "A line of text content";  // add text
container.appendChild(content);  // append to parent div
```

When the `js` file runs the DOM tree will look like
```html
<!-- HTML file -->

<body>
	<h1>TITLE OF WEBPAGE</h1>
	<div id="container">
		<div class="content">A line of text content</div>
	</div>
</body>
```

`js` will not alter the html file, it just affects how the browser renders the content.

`js` should run after the DOM tree and its nodes are created otherwise it will not work properly. To avoid issues, `js` is included at the end of the html file or,
the `js` file can be linked in the `<head>` of the file with keyword `defer` to load the file after the HTML is parsed.
```html
<head>
	<script src="file.js" defer></script>
</head>
```
more about [`defer`attribute for script tag](https://javascript.info/script-async-defer#defer)





# Exercise

Add the following elements to the container using ONLY JavaScript and the DOM methods shown above:

1. a `<p>` with red text that says “Hey I’m red!”
2. an `<h3>` with blue text that says “I’m a blue h3!”
3. a `<div>` with a black border and pink background color with the following elements inside of it:
    - another `<h1>` that says “I’m in a div”
    - a `<p>` that says “ME TOO!”
    - Hint for this one: after creating the `<div>` with createElement, append the `<h1>` and `<p>` to it before adding it to the container.

