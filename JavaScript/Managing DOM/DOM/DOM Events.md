Manipulating DOM dynamically or on demand

[[7 DOM Events]] in HTML

# Events

Events are actions that occur on the webpage such as mouse click or key press.
Using `js` we can make the webpage listen and react to these events.

Three ways of doing this
* Specify function attributes directly on the HTML elements
* Set properties in the form of `on<eventType>`, such as `onClick` or `onmousedown` on the DOM nodes in the JavaScript
* Attach ***event listeners*** to the DOM nodes in your JavaScript

Event Listeners are the preferred method

## Method 1
```html
<button onclick="alert('Hello World!')">Click Me</button>
```
It clutters the HTML with JavaScript. Also it has one `onclick` property per DOM element, so no multiple separate functions.

Using it with named functions
```html
<button onclick="alertFunction()">Click Me</button>
```
```js
function alertFunction() {
	alert("Yay you cliked");
}
```

## Method 2
```html
<button id="btn">Click Me</button>
```
```js
const btn = document.querySelector("#btn");
btn.onclick = () => alert("Hello World");
```
`js` is out but still DOM element can only have one `onclick` property.

Using a named function
```html
<button id="btn">Click Me</button>
```
```js
function alertFunction() {
	alert("Yay you clicked");
}

btn.onclick = alertFunction;
```

## Method 3
```html
<button id="btn">Click Me</button>
```
```js
const btn = document.queryselector("#btn");
btn.addEventListener("click", () => {
	alert("Hello World");
});
```
This maintains a separation of concerns and we follow multiple event listeners if need arises.

```html
<button id="btn">Click Me</button>
```
```js
function alertFunction() {
	alert("Yay you clicked");
}

btn.addEventListener("click", alertFunction);

btn.addEventListener("click", function(e) {
	console.log(e);
});
```



# Callback

A callback is simply a function that is passed into another function as an argument.
When we pass in `alertFunction()` or `function(e){..}` as an argument to `addEventListener` this is a callback.

```js
btn.addEventListener("click", function(e) {
	console.log(e.target)
});

btn.addEventListener("click", function(e) {
	e.target.style.background = "blue";
});
```
The `e` parameter in that call back function contains an object that references the `event` itself. within that object you have access to many useful properties and methods(functions that live inside an object) such that which mouse button or key was pressed, or information about the even's `target`- the DOM node that was clicked. ????


## Attaching Listeners to group of nodes

We can get a NodeList of all the items matching a specific selector with `querySelectorAll("selector")`.
In order to add listeners to each of them, we need to iterate through the whole list.

```html
<div id= "container">
	<button id="one">Click Me</button>
	<button id="two">Click Me</button>
	<button id="three">Click Me</button>
</div>
```
```js
const buttons = document.querySelectorAll("button");
// buttons is now a nodelist, somewhat like an array

// using .forEach method to iterate through each button 
buttons.forEach( (button) => {
	button.addEvenetListener("click", () => {
		alert(button.id);
	// for each one we add a 'click' listener
		});
});
```



## DOM Events

These allow `js` to add `eventListener` or `eventHandler` to HTML elements.

Here in HTML, `onclick` is the event listener and `myFunction()` is the event handler
```html
<button onclick="myFunction()">CLick Me</button>
<button onclick="alert('hello')">CLick Me</button>
```
In this `JS`, click is the event listener and `myFunction` is the event handler
```js
button.addEventListener("click", myFunction);
```

[Explanation on other Events](https://www.w3schools.com/jsref/dom_obj_event.asp)  like click, dbclick, keydown, keyup


[[shopping list Excersice]]


Other Events 
- [JavaScript events](https://www.javascripttutorial.net/javascript-dom/javascript-events/)
- [Page load events](https://www.javascripttutorial.net/javascript-dom/javascript-page-load-events/)
- [Mouse events](https://www.javascripttutorial.net/javascript-dom/javascript-mouse-events/)
- [Keyboard events](https://www.javascripttutorial.net/javascript-dom/javascript-keyboard-events/)
- [Event delegation](https://www.javascripttutorial.net/javascript-dom/javascript-event-delegation/)
- [The dispatchEvent method](https://www.javascripttutorial.net/javascript-dom/javascript-dispatchevent/)
- [Custom events](https://www.javascripttutorial.net/javascript-dom/javascript-custom-events/)




### [Additional resources](https://www.theodinproject.com/lessons/foundations-dom-manipulation-and-events#additional-resources)

This section contains helpful links to related content. It isn’t required, so consider it supplemental.

- [Eloquent JS - DOM](http://eloquentjavascript.net/13_dom.html)
- [Eloquent JS - Handling Events](http://eloquentjavascript.net/14_event.html)
- [DOM Enlightenment](http://domenlightenment.com/)
- [Plain JavaScript](https://plainjs.com/javascript/) is a reference of JavaScript code snippets and explanations involving the DOM, as well as other aspects of JS. If you’ve already learned jQuery, it will help you figure out how to do things without it.
- This [W3Schools](https://www.w3schools.com/js/js_htmldom.asp) article offers easy-to-understand lessons on the DOM.
- [JS DOM Crash Course](https://www.youtube.com/watch?v=0ik6X4DJKCc&list=PLillGF-RfqbYE6Ik_EuXA2iZFcE082B3s) is an extensive and well explained 4 part video series on the DOM by Traversy Media.
- [Understanding The Dom](https://www.digitalocean.com/community/tutorial_series/understanding-the-dom-document-object-model) is an aptly named article-based tutorial series by DigitalOcean.
- [Introduction to events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events) by MDN covers the same topics you learned in this lesson on events.
- [Wes Bos’s Drumkit](https://www.youtube.com/watch?v=VuN8qwZoego) JavaScript30 program reinforces the content covered in the assignment. In the video you will notice that a deprecated [keycode](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/keyCode) keyboard event is used, replace it with the recommended [code](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code) keyboard event and replace the `data-key` tags accordingly.
- [Event Capture, Propagation and Bubbling video](https://www.youtube.com/watch?v=F1anRyL37lE) from Wes Bos’s JavaScript30 program.
- [Understanding Callbacks in JavaScript](https://dev.to/i3uckwheat/understanding-callbacks-2o9e) for a more in-depth understanding of callbacks.

