
### Fitting react into Website

The React core library is a UI library first and foremost. The core library alone is comparable to other UI libraries, but not directly comparable to more full-fledged web application frameworks such as Angular.

It’s very difficult and bordering on impossible to create a hybrid SPA with some parts rendered by, for example, Angular or Vu, and others by React.

You can use React for just part of your UI if you have a website with smaller interactive UI elements (or widgets). In such a case, you can replace your widgets one by one with small React applications, without changing everything else.

React is backend agnostic for frontend development. In other words, you don’t have to rely on a JavaScript-based backend (Node or Deno) to use React.


___

Another popular use case for React is for static site generators. In such a setup, React is used to define your website locally on your environment, but when deployed
to the live server, it’s rendered “down” to a plain HTML website with JavaScript only doing a minimal bit of work to add interactivity. All your templates, and so on, will
have been resolved. Initially, this was mostly popular for smaller websites, such as blogs, which don’t update too frequently.

___

To summarize how React fits into a website, it’s most often used in these scenarios:
* As a UI library in an SPA, such as React+React Router+Redux
* As a drop-in widget in any frontend stack, such as a React autocomplete input component in a website built using any other combination of technologies
* As a static website rendered on deployment to serve infrequently updated content
* As a UI library in mobile apps using React Native, or desktop apps using Electron

___

### Single-page applications and React

A website is considered an SPA if it has a lot of
functionality directly available in the browser and not just information. 

Examples include Facebook, Google Docs, Gmail, and so on.

SPAs are built using a multitude of technologies, of which React is only one potential part in the stack. You can’t even use React alone; at least a few other technologies are needed for React to be usable as a standalone application.

SPAs are also known as thick clients because the browser, being a client, holds more logic and performs functions such as rendering of the HTML, validation, UI changes, and so on. 

Contrast this with a thin client, where the browser client is only used to display information that has been pre-rendered by a server. In a thin client, the browser does very little work.

* The user types a URL in the browser to open a new page. 
* The browser sends a URL request to the server.
* The server responds with static assets such as HTML, CSS, and JavaScript. In most cases, the HTML is bare-bones; that is, it has only a skeleton of the web page. Usually, there’s a “Loading . . . ” message and/or rotating spinner GIF.
* The static assets include the JavaScript code for the application. When loaded, this code makes additional requests for data.
* The data comes back in JSON, XML, or any other format.
* Once the application receives the data, it can render missing HTML (the User Interface block in the figure). 
* Once the browser rendering is finished, the browser updates the displayed content, and the user can work with the application.
* The user sees a beautiful web page.

> [!hydaration]
> The process of rendering the UI occurs within the browser as the application injects data into pre-rendered templates, also known as hydration.


To summarize, in an SPA, most rendering for UIs happens in the browser. Only data travels to and from the browser. Contrast that with a “classic” website, which is not an SPA, where all the rendering happens on the server.

React fits into this SPA architecture by rendering content based on data as well as handling user input and updating the content based on the updated data that results from these inputs.


___

### The React Stack

React is minimalistic in the sense that it only does a single job rendering reactive UIs.

While you can use React as a smaller part of your stack, developers most often opt to use a React-centric stack, which consists of the React core itself as well as data, routing, and styling libraries created to be used specifically with React,

* Data model libraries and backends—Examples include TanStack Query (https://tanstack.com/query/latest), Redux (http://redux.js.org), Recoil.js (https://recoiljs.org/), XState (https://xstate.js.org/), and Apollo (www.apollographql.com/)

* Routing library—Often React Router (https://github.com/remix-run/react-router) or a similar router implemented in many frameworks

* Styling libraries—Either a predefined set of styled components such as Material UI (https://mui.com/) or Bootstrap (https://react-bootstrap.github.io/) or a library to easily work with CSS inside React components, such as Styled-Components (https://styled-components.com/), Vanilla Extract (https://vanilla-extract.style/), or even Tailwind CSS (https://tailwindcss.com/)

___

React’s ability to describe composable components (self-contained chunks of the UI) enables code reuse. Many components are packaged as npm modules.

A great (curated) list of a lot of various React components for many purposes can be found here: https://github.com/brillout/awesome-react-components. 

This list has everything from UI components (including tons of form elements) to complete UI frameworks to development utilities and testing tools.

___

Another category of React frameworks is the full-blown server-side framework, which takes care of everything for you. Such frameworks come in two variants

* Gatsby—This very popular blogging framework is also useful for many other types of static websites.
* Next.js—As probably the most popular React website framework out there, this is useful for both small static websites and huge dynamic behemoths.
* Remix—This fairly new kid on the block is gaining traction and popularity very quickly in serving super-fast dynamic React websites.

___

JSX is optional 

Although all React developers write React using JSX, browsers will only run standard JavaScript and not understand JSX directly. That’s why it’s beneficial to be able to understand React code in pure JavaScript.

```html
<!DOCTYPE html>
<html>
	<head>
		<title>My First React Application</title>
		<script src="//unpkg.com/react@18/umd/react.development.js">
		 </script>

		<script src="//unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
	</head>

	<body>
		<div id="root"></div>
		
		<script type="text/javascript">
			...
		</script>
	</body>
</html>
```

First two scrips are importing React library and ReactDOM library.

By including the libraries in the HTML file, you get access to the React and React-DOM global objects: `window.React` and `window.ReactDOM`.
You’ll need two methods from those objects: one to create an element and another to render it in the
`<div>` container.

Div element is used to mount the React UI. Mounting to the body directlt will lead to conflict with other libraries and extensions.

#### Creating the React Element

The java Script part will contain
```js
const reactElement = React.createElement(
	'h1', null, 'Hello world!!' );

const domNode = document.getElementById('root');

const root = ReactDOM.createRoot(domNode);

root.render(reactElement);
```

Call `React.createElement(elementName, data, children)` with three arguments that have the following meanings:
* elementName—HTML tag as a string (e.g., 'h1') or a custom component class as an object. We don’t have any custom components just yet.
* data—A data object containing attributes and properties for the element. We don’t need any properties now, so we just pass null.
* children—Child elements or inner HTML/text content. In this example, it’s just “Hello world!!!”.

This listing gets a React element and stores the reference to this object in the reactElement variable. The reactElement variable isn’t an actual DOM node; rather, it’s an instantiation of the React h1 component (element).


Then get the DOM element with ID 'root', 

`const root = ReactDOM.createRoot(domNode);`
Creates a root holder for the React application connected to the specific DOM element.

`root.render(reactElement);` renders the h1 element into the root holder.

___

More consice version
```js
ReactDOM
.createRoot(document.getElementById('root'))
.render(React.createElement('h1', null, 'Hello world!'));
```

___

We need to serve the content using a local development web server.
Node will take care of setting up the server, just type `npx serve` in the folder with the `index.html`

>[!note]
>Due to cross-origin restrictions, you can’t open a file located on your local hard drive in the browser and have it access content on other domains (such as the React libraries loaded from https://unpkg.com). Browsers simply don’t allow this.

Alternatively other platforms can also be used.

```bash
$ npx http-server -p 3000

$ python -m http.server 3000

$ php -S localhost:3000
```

___

