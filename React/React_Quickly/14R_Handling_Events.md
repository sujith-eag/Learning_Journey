## Handling Events in React

Events are the way that users interact with a JavaScript web application. Events can
be caused by mouse movement or clicking, touch interface clicks and drags, key-
board button presses, scrolling, copying and pasting, as well as indirect interactions
such as focusing and unfocusing elements or the entire application.

Our web application creates JavaScript XML (JSX), which is converted to HTML. The user then
interacts with that HTML, and the result of those interactions are events dis-
patched from the HTML elements to our React application.

___

There are two ways to handle events in React:
* You can use React to manage your event listener.
* You can manually add and remove your event listener directly on a DOM node.

___

The API is very simple. If you define a property on a JSX element that references
an HTML node, and that property matches a known event from React’s list of sup-
ported events, React will treat the property as an event listener rather than as a DOM
attribute. React will then make sure to correctly add and remove the event listener, as
the component mounts and unmounts.

`onClick={function}`

___

a component that shows a checkmark if the mouse is moving around inside the element, but changes to a cross if the mouse has stopped moving for half a second or if the mouse moved outside the element.

we need to listen for the `mousemove` event.

```jsx
import { useState, useEffect } from 'react';

function MouseStatus() 
{
	const [isMoving, setMoving] = useState(false);
	const onMouseMove = () => setMoving(true);
	{/* local function to change the state when called*/}
	
	useEffet( () => { 
		if(!isMoving) return;
		
		const timeout = setTimeout( 
			() => setMoving(false), 500);
{/* setting moving state to false every half second */}
		return () => clearTimeout(timeout);
	} ,[isMoving]); // dependency array
	return (
		<section onMouseMove={onMouseMove}>
			<h2>
				The mouse is {!isMoving && "not"} moving: {isMoving ? "✓" : "✗"}
			</h2>
		</section>
	);
}

function App()
{
	return <MouseStatus />;
}
export default App;
```

___

Not all events are dispatched by all types of elements, though. Video (and audio) ele-
ments dispatch a play event once the video (or audio) starts playing. Buttons don’t dis-
patch that event because they aren’t videos (or audios) that play.

Let’s create an application that displays a Play/Pause button next to a video. When
the video is playing, the button is a Pause button; when the video is paused, the button
is a Play button.

For this, we need a total of four listeners. We need to listen to the play and pause
events on the video object, and we need to listen for the click event on our button, but
with two different event listeners depending on whether the video is playing or not.

```jsx
import { useState, useRef } from 'react';

const VIDEO_SRC = "....video source link";

function VideoPlayer()
{
	const [isPlaying, setPlaying] = useState(false);
// toggles for switching play state
	const onPlay = () => setPlaying(true); 
	const onPause = () => setPlaying(false);
	
	const onClickPlay = () => video.current.play();  // to play video on click
	const onClickPause = () => video.current.pause();
	
	const video= useRef();
	
	return (
		<section>
			<video 
				src={VIDEO_SRC}
				ref={video}
				controls
				width="480"
				onPlay={onPlay}
				onPause={onPause}
			/>
		</section>
		
		<button onClick={
			isPlaying ? onClickPause : onClickPlay
			}>{isPlaying ? "Pause" : "Play"}
		</button>
	);
}

function App()
{
	return <VideoPlayer />;
}
export default App;
```

___

Listening to events in React is really only about three things:
* Knowing what event to listen for
* Knowing which element to listen on
* Assigning a listening function to the correct property on the correct element

___

#### Events supported by React

if you set a property on a JSX element that matches a known event type, React will convert that property to a listener on that element, regardless of whether that element can dispatch that event at all. You can, assign an onPlay event listener to an `<h1 />` element, even though that event will only ever be dispatched from `<video />` and `<audio />` elements.


* Clipboard Events : `onCopy, onCut, onPaste`
* Keyboard events : `onKeyUp`, `onKeyDown`, `onKeyPress`
* Focus events : `onFocus`, `onBlur`
* Form events : `onChange`, `onInput`, `onInvalid`, `onReset`, `onSubmit`
* Composition Events : `onCompositionStart`, `onCompositionEnd`, `onCompositionUpdate`
* Generic events : `onError, onLoad`
* Mouse events : `onClick onContextMenu onDoubleClick onDrag onDragEnd` `onMouseEnter onMouseLeave` `onMouseMove onMouseOut onMouseOver onMouseUp` 
* Pointer events : `onPointerDown onPointerMove onPointerUp onPointerCancel` `onGotPointerCapture` `onLostPointerCapture onPointerEnter onPointerLeave` `onPointerOver onPointerOut`
* Selection events : `onSelect`
* Touch events : `onTouchCancel onTouchEnd onTouchMove onTouchStart`
* UI events : `onScroll`
* Wheel events : `onWheel`
* Media events : `onAbort onCanPlay onCanPlayThrough onDurationChange` `onEmptied onEncrypted` `onEnded onError onLoadedData onLoadedMetadata onLoadStart` `onPause onPlay` `onPlaying onProgress onRateChange onSeeked onSeeking` `onStalled onSuspend` `onTimeUpdate onVolumeChange onWaiting`
* Image events : `onLoad onError`
* Animation events : `onAnimationStart onAnimationEnd onAnimationIteration`
* Transition events : `onTransitionEnd`
* Other events : `onToggle`

___

#### Definition of event handlers

You can define the event function any way you like. If it’s a valid function, it’s valid as
an event handler. Common options include the following:
* Define the function as a local variable using an arrow function.
* Define the function as a local variable using a function expression.
* Define the function as an inline function using an arrow function directly assigned to the property.

Using arrow function to create a variable and assigning it as onClick property
```jsx
function Counter() 
{
	const [counter, setCounter] = useState(0);
	const onClick = () => setCounter(c => c + 1);
	return (
		<>
			<h1>Value: {counter}</h1>
			<button onClick={onClick}>Increment</button>
		</>
	);
}
```

defining with function expression 
```jsx
function Counter() 
{
	const [counter, setCounter] = useState(0);
	function onClick() {
		setCounter(c => c + 1);
}

	return (
		<>
			<h1>Value: {counter}</h1>
			<button onClick={onClick}>Increment</button>
		</>
	);
}
```

same component with the handler defined inline using an arrow function:
```jsx
function Counter()
{
	const [counter, setCounter] = useState(0);
	
	return (
		<>
			<h1>Value: {counter}</h1>
			<button onClick={() => setCounter(c => c + 1)}
			>Increment
			</button>
		</>
	);
}
```

A common convention is to define single-line event handlers inline, but multiline event handlers in a separate variable.

```jsx
const onClick = () => 
{
	setCounter(count => count + 1);
	toggleState();
};
return <button onClick={onClick}>Button</button>;
```

___

Using a Single event handler to handle increment and decrement.

To do this, we need to know which button caused the event that was sent to the event handler. We can do that by looking at the event object passed. It will have a property,`.target`, that points to the HTML node that was clicked. 

To compare this target property with the actual node, we need a reference to one of the nodes in our component.

```jsx
import { useState, useRef } from 'react';

function Counter()
{
	const [counter, setCounter] = useState(0);
	
	const increment = useRef();
	// reference to one node

// evt is the event object passed from event
	const onClick= (evt) => {
		const delta = 
			evt.target === increment.current ? 1 : -1;
	// if it is not increment then it is the other
		setCounter( (value) => value + delta);	
	};
	return (
	<section>
		<h1>Value: {counter}</h1>
		<button ref={increment} onClick={onClick}>
			Increment
		</button>
		<button onClick={onClick}>
			Decrement
		</button>
	</section>
	);
}
function App()
{
	return <Counter />;
}
export default App;
```


> [!note]
> Event objects always have a target property that refers to the target of the event. Another property that all events have is the type property. The value of this property is the type of event invoked.

we assigned the same event handler to both
the onMouseEnter and the onFocus property of an input field. Then, our event handler would fire if the user either moved their mouse over the field or used the keyboard to tab into the field. We could tell which event occurred by looking at the
`evt.type` property.

___


React already listens to all events on all nodes.
when you add a listener to a JSX element, React doesn’t add a new listener anywhere. Instead, it just remembers that you want to be informed about this specific type of event for this specific node.

___

#### Event phases and propagation


Every event in React bubbles up through all the nodes in the document tree above it. 

To know which section has focus, we just need to listen for when anything inside a section receives focus. Likewise, to know that an element loses focus, we just need to know whenever any element inside the form loses focus. We can use this trick to place our focus listeners on the two sections and the blur listener on the form itself

When you focus any input field, the event will first dispatch on the input field itself, but after that, the same event will dispatch on every ancestor to the target element in order from the parent all the way up to the root node of the React application.

When the bubbling reaches the field set, React will invoke our onFocus listener placed there. Similarly, when an input blurs, React will invoke the onBlur listener placed on the form element.

```jsx
import { useState } from "react";
const FOCUS_NONE = 0;
const FOCUS_USER = 1;
const FOCUS_REQUEST = 2;

function getStyle(isActive) 
{
	return {
		display: "flex",
		flexDirection: "column",
		backgroundColor: isActive ? "oldlace" : "transparent",
	};
}

function Field({ label, children }) 
{
	return (
		<label>
			{label}:
			<br />
			{children}
		</label>
	);
}

function Contact() 
{
	const [focus, setFocus] = useState(FOCUS_NONE);
	
	const onUserFocus = () => setFocus(FOCUS_USER);
	const onRequestFocus = () => setFocus(FOCUS_REQUEST);
	const onBlur = () => setFocus(FOCUS_NONE);

	return (
		<form onBlur={onBlur}>
			<h1>Contact</h1>
			<fieldset
				onFocus={onUserFocus}
				style={getStyle(focus === FOCUS_USER)}>			
				<legend>User</legend>
				<Field label="Name">
					<input />
				</Field>
				<Field label="Email">
					<input type="email" />
				</Field>
			</fieldset>

			<fieldset
				onFocus={onRequestFocus}
				style={getStyle(focus === FOCUS_REQUEST)}>
				<legend>Request</legend>
				<Field label="Subject">
					<input />
				</Field>
				<Field label="Body">
					<textarea />
				</Field>
			</fieldset>
		</form>
	);
}

function App() {
	return <Contact />;
}
export default App;
```

___

#### Default browser behaviour

a button inside a form causes the form to submit, and when a form submits, the variables inside the form will be sent to the target URL of the form. This happens even if the form doesn’t have any inputs and even if the form doesn’t have an explicit target URL (the default target URL is the page itself)

```jsx
import { useState } from "react";
function Admin() 
{
	const [password, setPassword] = useState("");
	const [isAdmin, setAdmin] = useState(false);
	const onClick = () => {
		if (password === "platypus") {
			setAdmin(true);
		}
	};
	
	return(
		<>
		{isAdmin && <h1>Secret message</h1>}
			 {/* Conditional Display*/}
		<form>
			<input
				type="password"
				onChange={
					(evt) => setPassword(evt.target.value)
				}
			/>
			
			<button onClick={onClick}>
				Login
			</button>
		</form>
		</>
	);
}

function App()
{
	return <Admin />;
}
export default App;
```

This causes the hole page reloads, and the input field is cleared. since button is inside the form.


#### Preventing default

First, we’ll move the event handler from clicking the button to submitting the form. We just assign it to the `onSubmit` property of the form rather than the `onClick` property of the button.

Second, we need to tell the form not to perform the default action that it normally does when submitting. We do that by invoking `evt.preventDefault()` on the event object passed to the event handler.

```jsx
import { useState } from "react";
function Admin() 
{
	const [password, setPassword] = useState("");
	const [isAdmin, setAdmin] = useState(false);
	const onSubmit = (evt) => {
		evt.preventDefault();
		if (password === "platypus") {
			setAdmin(true);
		}
	};
	
	return isAdmin ? (
		 <h1>Secret message</h1> 
		 ) : (
		<form onSubmit={onSubmit}>
			<input
				type="password"
				onChange={
					(evt) => setPassword(evt.target.value)}
			/>
			<button>
				Login
			</button>
		</form> 
	);
}

function App()
{
	return <Admin />;
}
export default App;
```

___

#### Other default events

Form submit events have a default action, where the form actually submits to the target URL with all the values entered into the form.

Clicking a link will create a click event on the link element. The default action for this event is to follow the link and go to the new 

URL as indicated by the href property. Again, you can prevent this default behavior by invoking the `.preventDefault()` method on the click event object received in an event handler. This would mean the browser wouldn’t go to the target URL, and effectively nothing would happen.


if an event is cancellable by checking the `.cancellable` property. If true, `.preventDefault()` can be invoked to stop whatever the browser’s default action would have been.

Scroll events are cancellable, which causes the scroll not to occur and the scroll offset to remain unchanged.

Key-down, key-press, and key-up events are cancellable and cause the character to not be inserted

#### React event objects in summary

number of different ways to use the event object that React sends to an event handler.

Booleans 
bubbles: A Boolean value indicating whether or not the event bubbles

cancelable : A Boolean value indicating whether or not the event can be canceled

preventDefault : A method to prevent the browser from handling the event with its default action

stopPropagation :  method to prevent the event from propagating any further

target : The target node that this event was assigned to

timestamp : The time at which the event was created in milliseconds

type : The type of event that caused this event object to be dispatched


___

#### Event handler functions from properties


```jsx
import { useState } from "react";

function Button({ handleClick, label }) 
{
	const buttonStyle = {
		color: "blue",
		border: "1px solid",
		background: "transparent",
		borderRadius: ".25em",
		padding: ".5em 1em",
		margin: ".5em",
	};

	return (
		<button style={buttonStyle} onClick={onClick}>
			{label}
		</button>
	);
}

function StyledCounter() 
{
	const [counter, setCounter] = useState(0);
	const update = (d) => setCounter((v) => v + d);
	return (
			<section>
				<h1>Counter: {counter}</h1>
				<div>
				<Button
					handleClick={() => update(1)}
					label="Increment"
				/>
				<Button
					handleClick={() => update(-1)}
					label="Decrement"
				/>
			</div>
		</section>
		);
	}
function App() {
	return <StyledCounter />;
}
export default App;
```

we’ve named the event listener as a property `handle*`. That is a fairly common practice when passing functions as properties to elements that aren’t directly event listeners themselves, but rather just callbacks that will be invoked by event listeners or effects as needed.



We’ll use on* naming for direct event handlers (that receive an event object) and handle* naming for callbacks (that either don’t take any arguments or take some custom arguments).


___


### Event handler generators

If you have many event handler functions that only vary slightly, you might want to generalize them into an event handler generator.

```jsx
function Counter() {
const [counter, setCounter] = useState(0);
const update = (delta) =>
setCounter((c) => c + delta);
return (
<>
<h1>Value: {counter}</h1>
<button onClick={() => update(1)}>
Increment
</button>
<button onClick={() => update(-1)}>
Decrement
</button>
</>
);
}
```

```jsx
function Counter() {
const [counter, setCounter] = useState(0);
const update = (delta) => () =>
setCounter((c) => c + delta);

return (
<>
<h1>Value: {counter}</h1>
<button onClick={update(1)}>Increment</button>
<button onClick={update(-1)}>Decrement</button>
</>
);
}
```

### Listening to DOM events manually


An expandable menu that doesn't close when clicked inside also

```jsx
import { useRef, useState, useEffect } from "react";
function Menu() {
const [isExpanded, setExpanded] = useState(false);
useEffect(() => {
if (!isExpanded) {
return;
}
const onWindowClick = () => setExpanded(false);
const onMenuClick = (evt) => evt.stopPropagation();
const menu = menuRef.current;
window.addEventListener("pointerdown", onWindowClick);
menu.addEventListener("pointerdown", onMenuClick);
return () => {
window.removeEventListener(
"pointerdown", onWindowClick
);
menu.removeEventListener(
"pointerdown", onMenuClick
);
};
}, [isExpanded]) ;

const menuRef = useRef();
return (
<main>
<button onClick={() => setExpanded(true)}>Show menu</button>
{isExpanded && (
<div ref={menuRef}
style={{ border: "1px solid black", padding: "1em" }}
>This is the menu</div>
)}		
</main>
);
}
function App()
{
	return <Menu />;
}
export default App;
```


___
