### Events

Another common example of using an effect only for mount and unmount is listening for events. 

For example, you might want your component to update itself when the whole web page resizes (listening to the resize event) or when a certain element scrolls (listening to the scroll event).

#### Cancelling Action if Unmounted

The third type of use case for mount and unmount is when data is being loaded when mounted,if the user navigates away before response came in, we would be trying to update state on a component that no longer exists.

This can be mitigated in one of two ways: you can either cancel the request in a cleanup function (in JavaScript, via `AbortController`), or you can have a local flag that remembers whether the component is still mounted and only updates the component state if the flag is true. If not, the component just ignores the returned response.

____

Canceling the request using an AbortController on unmount.

```jsx
useEffect( () => {
	const controller = new AbortController();
	// creating abort controller inside effect
	
	fetch(url, { controller }) // passing abort to fetch
		.then( data =>{
			// handle the data
		});
	return () => { // cleanup function
		controller.abort() };
	};
}, [] );
```

____

#### Running cleanup on unmount


A much more common use case for the cleanup function is to do exactly what it’s named for: clean up after a `useEffect` that leaves some sort of functionality in place after it unmounts, in order to not misuse resources or have memory leaks in our application.

#### Running an application on some renders

This time, we’ll utilize the dependency array. We want our effect to run on mount, but also every time a certain property changes. However, we don’t want it to run just because other properties change, so we’re careful about including only the relevant variables in the dependency array.

```jsx
import { useEffect } from 'react';

function BlogPost( {title, body} )
{
	useEffect( () => {
		document.title = title; {/*Effect to change the title*/}
	}, [title] );
	{/*document updated when the post title is*/}
	return (
		<article>
			<h1>{title}</h1>
			{body}
		</article>
	);
}

function App()
{
	return (
		<main>
			<BlogPost
				title="first post"
				body={<p>welcome to this website</p>} />
		</main>
	);
}
export default App;
```

This is probably the perfect textbook example of what useEffect is meant for, that is, to execute side effects of a component. 

You can’t update the document title through the DOM, so it has to be a side effect; for that, useEffect is the perfect solution.

___

#### Updating from a Property

Another common use case is to update a state value based on a property.


A state in useState to the value of a property, it is only set to that property when the component renders the first time around on mount. If the component later re-renders with a new property value, the state won’t automatically update to that value.

We can fix that using an effect that depends on the value of the property and updates the state value based on it.

```jsx
import { useEffect, useState } from "react";

function EmailInput({ value }) 
{
	const [email, setEmail] = useState("");
	useEffect( () => setEmail(value), [value] );
	{/*only value poperty is added to the 
	dependency array, so every render where 
	property value changes, the email state
	is reset*/}
	
	return(
		<label>
			Email address: <input
			type="email"
			value={email}
			onChange={ (evt) => setEmail(evt.target.value) }
			/>
	{/*Update state value when input changes*/}
		</label>
	);
}

const EMAIL1 = "daffyduck@looneytunes.invalid";
const EMAIL2 = "bugsbunny@looneytunes.invalid";
const EMAIL3 = "elmerfudd@looneytunes.invalid";

function App() 
{
	const [defaultEmail, setDefaultEmail] = useState(EMAIL1);
	return (
		<main>
			<button 
				onClick={() => setDefaultEmail(EMAIL1)}>Use {EMAIL1}
			</button>
			<br />
			<button 
				onClick={() => setDefaultEmail(EMAIL2)}>Use {EMAIL2}
			</button>
			<br />
			<button 
			onClick={() => setDefaultEmail(EMAIL3)}>Use {EMAIL3}
			</button>
			<br />
			
			<EmailInput value={defaultEmail} />
	</main>
	);
}
export default App;
```


___

#### Running an effect and cleanup on some renders

A countdown component is an example of a component in which we want to run cleanup on unmount.

The countdown component will be initialized with the starting time of the counter, which is 10 in this example. It also has a Reset button that will reset the counter to the initial value at any point. Furthermore, there’s a Pause/Resume button that will toggle whether the counter is running or not. 

Finally, there’s the actual countdown decreasing every second, pausing the counter once it reaches 0. To make sure we can’t start the counter again at 0, the Pause/Resume button is disabled if the countdown is over.

```jsx
import { useEffect, useState } from 'react';

function Countdown( {from} )
{
	const [seconds, setSeconds] = useState(from);
	const [isRunning, setRunning] = useState(false);
	
	useEffect( () => {
		if(!isRunning) {
			return; 
		}
		const interval = setInterval(
			() => setSeconds( 
				(value) => { if (value <= 1) 
					{ setRunning(false); }
				return value-1;
				}) ,1000);
		return ()=> clearInterval(interval);
		}, [isRunning] );
		
		
		return (
			<section>
				<h2>Time left: {seconds} seconds</h2>
				<button onClick={() => setSeconds(from)}>
					Reset
				</button>
				<button
					onClick={() => setRunning((v) => !v)}
					disabled={seconds === 0}
					>{isRunning ? "Pause" : "Resume"}
				</button>
			</section>
		);
	}
function App() {
	return <Countdown from={10} />;
}
export default App;
```

Initialize the seconds to value of property, and isRunning flag to false.

We make our effect depend on the value of the isRunning state value. Whenever this value changes, our effect runs (and the cleanup of the last effect runs just before it).

The first thing we check in the effect is whether the countdown is running at all. If not, we just abort silently (and return  nothing—nothing to clean up).

If the countdown is running, we define an interval that updates the state value every second. When we update the state value, we check if the value was 1 (or less); if so, we make sure to stop the countdown.

Return one less than the current value of the counter.

Ensures our effect returns a cleanup function that cancels the interval completely.

In our component JSX, we have a button that resets the counter and only that (it doesn’t change the value of the run flag).

Another button flips the value of the run flag but doesn’t change the counter. This button is disabled, however, if the counter is at zero.
We vary the text on the toggle button depending on the current state of the run flag.

___

One thing you might notice is that when our counter reaches zero, we don’t directly stop the interval. we toggle the running flag to false with `setRunning(false)`;. Doing so will force our component to re-render, causing the effect to rerun because isRunning is listed as a dependency for the effect. As the effect reruns, the cleanup function will stop the interval. So, setting the isRunning flag to false will indirectly stop the  interval, but only through the magic of the hook.


___

#### Running an effect synchronously

What if we instead could run an effect after React generates the required HTML but before the browser updates the UI and displays it to the user.

We can run a layout effect hook instead, which does two things differently than the regular effect hook. First, it runs before the browser updates the UI, but—just as important—it also runs instantly as the DOM is generated.

`useEffect` is the correct hook to use in almost all use cases. It’s identical to `useEffect` in every way except when it’s called.

`useLayoutEffect` is called synchronously in the same execution cycle as when the components are rendered into the DOM (but before the browser
has had a chance to paint the DOM to the browser window). 

On the other hand, `useEffect` is invoked asynchronously on the next execution cycle where the DOM has been painted to the window and all CSS has taken effect and been calculated.

___


