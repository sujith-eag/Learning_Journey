
# Handling Side Effects

Most real apps that you will build as a React developer also need to send HTTP requests, access the browser storage and log analytics data, or perform any other kind of similar task, and with components, props, events, and state alone, you’ll often encounter problems when trying to add such features to your app. 

Actions that are not directly related to producing a (new) user interface state often clash with React’s component rendering cycle. They may introduce bugs or even break the entire web app.


Side effects are actions or processes that occur in addition to another main process.

If the HTTP request were sent upon a click of a button rather than as part of the main component function body, it would not be a side effect.

A `<button>` added to the JSX code. This button invokes a newly added `handleFetchPosts()` function, which then sends the HTTP request (and updates the state).
```jsx
import { useState } from 'react';

import classes from './BlogPosts.module.css';

async function fetchPosts() {
	const response = await fetch('https://jsonplaceholder.typicode.com/posts');
	const blogPosts = await response.json();
	return blogPosts;
}

function BlogPosts() {
	const [loadedPosts, setLoadedPosts] = useState([]);
	function handleFetchPosts() {
		fetchPosts().then((fetchedPosts) => setLoadedPosts(fetchedPosts));
	}
	
	return (
		<>
			<button onClick={handleFetchPosts}>Fetch Posts</button>
			<ul className={classes.posts}>
				{loadedPosts.map((post) => (
					<li key={post.id}>{post.title}</li>
		))}
			</ul>
		</>
	);
}

export default BlogPosts;
```

With this change made, the HTTP request is not sent every time the component function re-renders (that is, is executed again). Instead, it’s only sent whenever the button is clicked, and therefore, this does not create an infinite loop. The HTTP request, in this case, also doesn’t postulate a side effect, because the primary goal of `handleFetchPosts()` (i.e., the main process) is to fetch new posts and update the state.


In general, any action that’s started upon the execution of a React component function is a side effect if that action is not directly related to the main task of rendering the component’s user interface.

Here’s a non-exhaustive list of examples of side effects:
* Sending an HTTP request (as shown previously)
* Storing data to or fetching data from browser storage (for example, via the built-in localStorage object)
* Setting timers (via setTimeout()) or intervals (via setInterval())
* Logging data to the console via console.log()

Not all side effects cause infinite loops, however. Such loops only occur if the side effect leads to a state update.

