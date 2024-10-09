# Scripts: async, defer

When script runs before the DOM is loaded
1. Scripts can’t see DOM elements below them, so they can’t add handlers etc.
2. If there’s a bulky script at the top of the page, it “blocks the page”. Users can’t see the page content till it downloads and runs:

The simple solution is to keep the script file at the end but this solution is far from perfect. 
For example, the browser notices the script (and can start downloading it) only after it downloaded the full HTML document. For long HTML documents, that may be a noticeable delay.

There are two `<script>` attributes that solve the problem for us: `defer` and `async`.



# defer
he `defer` attribute tells the browser not to wait for the script. Instead, the browser will continue to process the HTML, build DOM. The script loads “in the background”, and then runs when the DOM is fully built.

- Scripts with `defer` never block the page.
- Scripts with `defer` always execute when the DOM is ready (but before `DOMContentLoaded` event).
- The page content shows up immediately.
- `DOMContentLoaded` event handler waits for the deferred script. It only triggers when the script is downloaded and executed.
```html
<p>..content before script..</p>

<script defer src="....js"></script>
```

**Deferred scripts keep their relative order, just like regular scripts.**
Browsers scan the page for scripts and download them in parallel, to improve performance. 

```html
<script defer src="long.js"></script>
<script defer src="small.js"></script>
```
So even though small.js loads first, it still waits and runs after long.js executes so it ensures that the relative order is kept.



# async

The `async` attribute means that a script is completely independent:

`async` scripts load in the background and run when ready. The DOM and other scripts don’t wait for them, and they don’t wait for anything. A fully independent script that runs when loaded. 

- The browser doesn’t block on `async` scripts (like `defer`).
- Other scripts don’t wait for `async` scripts, and `async` scripts don’t wait for them.
- `DOMContentLoaded` and async scripts don’t wait for each other:
    - `DOMContentLoaded` may happen both before an async script (if an async script finishes loading after the page is complete)
    - …or after an async script (if an async script is short or was in HTTP-cache)


with two scripts `long.js` and `small.js`, but now with `async` instead of `defer`. They don’t wait for each other. Whatever loads first (probably `small.js`) – runs first.
- async scripts run in the “load-first” order.



# Dynamic scripts
Creating scripts in `js` and appending it to the body when needed.
It starts loading as soon as it gets appended so dynamic scripts behave as async by default.
* They don't wait for anything, nothing waits for them
* the script that loads first - runs first.

```js
let script = document.createElement("script");
script.src = "/article/long.js";
document.body.append(script);
```





In practice, `defer` is used for scripts that need the whole DOM and/or their relative execution order is important.

And `async` is used for independent scripts, like counters or ads. And their relative execution order does not matter.