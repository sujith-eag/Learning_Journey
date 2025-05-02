

### Effects and React component life cycle

In React, everything that happens, happens in some component, so if your application wants to set a cookie, load some data, handle form input, display the user’s camera, start or stop a timer, or a myriad of other dynamic capabilities, you need more than just JSX.

Let’s say you have a timer component, and you want it to display the number of seconds it has been mounted. using a state value, which increments the counter every second, when you change the state value the whole component re-renders which starts another interval; rendering and every second it doubles. This is not the way to do it.

A component can re-render because a property changes or because it has multiple state values that can change independently of the counter. If your component unmounts because it isn’t needed anymore, the time-out continues to run and, after a second, will try to update a component that no longer exists. That’s unfortunately also not a good way to do it.

To solve this problem, React introduced an `effect` hook, called `useEffect`

#### Running effects in components

Effects are functions that run inside a component under
certain circumstances. To run an effect, you have to specify under which circumstances the effect should run. To fully understand this, we have to dive into the topic
of the React component life cycle.

An effect in a `useEffect` hook is triggered when any value in a set of dependencies changes.

when an effect in `useEffect` runs, it can define a cleanup function that should run in one of two cases: before the effect is triggered again or if the component unmounts.

```jsx
function Component() {
	useEffect(
		function effect() {
			// some effect here
			return function cleanup() {
				// some cleanup here
			};
		},
		[dependency1, dependency2,...]
	);
	// rest of component
}
```

The hook contains an optional effect as well as an optional cleanup function. The effect runs on mount, and the cleanup runs on unmount—if they’re defined, of course. Furthermore, if the effect has a dependency array, the cleanup and effect will also run every time any value reference in the dependency array changes.

you can set up your useEffect call so that you can define just the effect, just the cleanup function, or both, when it suits your needs. Furthermore, by carefully crafting the dependency array with the right values, you can trigger your effect and cleanup to run at exactly the desired instances.

There are five likely scenarios that you want your effect and cleanup function to run under. 

We’ll go through all five scenarios with examples of each:
* You’re loading some external data in a component. To correctly do that in an effect, you need it to run as your component mounts.
* You’re creating a timer using an interval. To achieve this, you need to run such an effect as your component mounts, but also clean it up again as your component later unmounts.
* ou want to track when a dialog is closed regardless of how it’s closed. To do this properly, you need to run such an effect only as your component unmounts.
* You want to update the browser window (or tab) title with the title of the page currently displayed. To achieve this in an effect, you need it to run every time the title property changes, but not when any other property changes, as long as the title remains the same.
* You want to run a timer but only if the timer is active as denoted by an isActive flag. To achieve this, you need to run such an effect and its cleanup every time the isActive flag changes, but not if other properties or values change, as long as the isActive flag remains the same.

___

#### Running an effect on mount

to create a drop-down component that loads data from an external server to be displayed in the drop-down. We need to load this data as an effect that runs on mount, and then it shouldn’t ever run again.

The execution of an effect hook when the effect is only desired as the component mounts. dependency array is kept empty, and there’s no cleanup function. This means that the effect is only ever executed on mount and never as the component re-renders.

```jsx
import { useState, useEffect } from "react";

function RemoteDropdown() 
{
{/* a state to to hold values once fetched */}
	const [options, setOptions] = useState([]);

{/*In effect hook loading url with movie character names*/}
	useEffect( () => {
		fetch("//www.swapi.tech/api/people")
			.then((res) => res.json())
			.then((data) => data.results)
			.then((characters) => characters.map(({ name }) => name))
			.then((names) => setOptions(names));
		}, [] );
{/* passing an empty dependency array so 
this effect runs only once*/}
	return (
		<select>
			{options.map( (option) => (
				<option key={option}>
					{option}
				</option>
				))}
		</select>
	);
}
function App()
{
	return <RemoteDropdown />;
}
export default App;
```



This is a pretty classic setup that you’ll often see in web apps loading data that is relevant only inside a small part of the overall application. It does have a small problem
though. What happens if, for some reason, the component unmounts before the response comes back from the server.

We’ll have to deal with that in a cleanup function.

___

#### Running an effect on mount and cleanup on unmount

We’ve been tasked with creating a stopwatch component. It should start an interval as soon as the component mounts that just keeps incrementing as time passes; however, if the component is ever unmounted in the future (e.g., because the user closes it), we must make sure to stop the interval. 

This requires an effect that runs on mount but also runs a cleanup function on unmount.

To make the effect hook activate with an effect and cleanup only on mount and unmount, respectively, you must add an empty dependency array to make sure that the effect and cleanup never runs just because the component is re-rendering.


```jsx
import { useState, useEffect } from "react";

function Stopwatch()
{
	const [seconds, setSeconds] = useState(0);

{/*Using browser setInterval function to invoke
the state increment function steadily*/}
	useEffect( () => {
		const interval = setInterval(
			() => setSeconds( (seconds) => seconds + 1),
			1000
		);
{/*Cancels ongoing interval in cleanup function
using built-in clearInterval function*/}
		return () => clearInterval(interval);
	}, [] );
	return <h1>Seconds: {seconds}</h1>;
}


function App()
{
	const [showWatch, setShowWatch] = useState(false);
	
	return(
		<>
			<button onClick={ () => setShowWatch(
				(b)=> !b )}
				> Toggle watch
			</button>
			
			{showWatch && <Stopwatch />}
		</>
	{/* conditionally render stopwatch to see
	 cleanup function do its job */}
	);
}
export default App;
```


Even though we’re using the variable `setSeconds` inside the effect, we don’t list it as a dependency because it’s a stable variable that doesn’t change. 

The state update function as returned by the `useState` hook is always the same function by reference. You can include it in the array, and the hook works the same.

If you find this part a bit too complex to remember, just include the function in the array.

______


