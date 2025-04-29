
Install npm

Install and start react
```bash
npx create-react-app lab-app
```

If error for permission happens, run this and then create app.
```
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned

Need to install the following packages:
create-react-app@5.1.0
```

___
#### Installation Process

```bash
npm warn deprecated inflight@1.0.6: This module is not supported, and leaks memory. Do not use it. Check out lru-cache if you want a good and tested way to coalesce async requests by a key value, which is much more comprehensive and powerful.

npm warn deprecated glob@7.2.3: Glob versions prior to v9 are no longer supported

npm warn deprecated fstream-ignore@1.0.5: This package is no longer supported.

npm warn deprecated uid-number@0.0.6: This package is no longer supported.

npm warn deprecated rimraf@2.7.1: Rimraf versions prior to v4 are no longer supported

npm warn deprecated fstream@1.0.12: This package is no longer supported.

npm warn deprecated tar@2.2.2: This version of tar is no longer supported, and will not receive security updates. Please upgrade asap.

create-react-app is deprecated.
```

```bash
You can find a list of up-to-date React frameworks on react.dev
For more info see:https://react.dev/link/cra
```

```bash
Installing react, react-dom, and react-scripts with cra-template...

Initialized a git repository.

Installing template dependencies using npm...
```

```bash
To address all issues (including breaking changes), run:
  npm audit fix --force

Run `npm audit` for details.

Created git commit.

Success! Created lab-app at /home/sujith/Desktop/labFiles/full_stack/day_01/lab-app
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd lab-app
  npm start

Happy hacking!
```

___
#### Basic App

cd into the app directory and `npm start`

The `index.js` file imports React from react,
ReactDom from react dom client

import the relavent css for the file(which have specific `classname=''`) 

import all the Components used in the index page using relative linking but no file extensions used.

create a variable which will be the Root variable.

within the root render the react components in a self closing tag.


```js
// index.js

import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```

Each component has to import required dependencies separately, image, css, but react is not needed since no rendering happens here.

```js
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```


```js
// index.css
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',
    monospace;
}
```

___

#### Rotating animation

```css
@media (prefers-reduced-motion: no-preference) {
    .code-logo {
        width: 80%;
        animation: App-logo-spin infinite 20s linear;
    }
  }
```

```js
import logo from './code.png';

<img src={logo} className="code-logo" alt="logo" />
```


___
