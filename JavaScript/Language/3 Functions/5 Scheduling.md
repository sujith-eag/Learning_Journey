
We may decide to execute a function not right now, but at a certain time later. That’s called “scheduling a call”.

There are two methods for it:
- `setTimeout` allows us to run a function once after the interval of time.

- `setInterval` allows us to run a function repeatedly, starting after the interval of time, then repeating continuously at that interval.

These methods are not a part of JavaScript specification. But most environments have the internal scheduler and provide these methods. In particular, they are supported in all browsers and Node.js.


# `setTimeout()`

```js
let timerId = setTimeout( func|code, [delay], [arg1], [arg2], ...)
```

`func|code` Function or a string of code to execute. Usually, that’s a function. 
For historical reasons, a string of code can be passed, but that’s not recommended.

`delay` before run, in milliseconds (1000 ms = 1 second), by default 0.

`arg1`, `arg2`… Arguments for the function

calling the function after 1 second
```js
function sayHi() {
	alert('Hello');
}

setTimeout(sayHi, 1000);
```

calling with arguments
```js
function sayHi(phrase, who) {
	alert( phrase + ', ' + who);
}

setTimeout(sayHi, 1000, "Hello", "John"); // Hello, John
```

If the first argument is a string, the `js` creates a function from it.
```js
setTimeout( "alert('Hello')", 1000);
//not recommended, so better to use arrow function instead.

setTimeout( () => alert('Hello'), 1000);
```

#### Pass a function, but don't run it
```js
setTimeout(sayHi(), 1000);  // wrong
```
That doesn’t work, because `setTimeout` expects a reference to a function. And here `sayHi()` runs the function, and the _result of its execution_ is passed to `setTimeout`.



# `clearTimeout(timerId)`

A call to `setTimeout` returns a “timer identifier” `timerId` that we can use to cancel the execution.
```js
let timerId = setTimeout(...);

clearTimeout(timerId);
```

we schedule the function and then cancel it. As a result, nothing happens.
```js
let timerId = setTimeout( () => alert("never happens"), 1000);
alert( timerId );  // timer identifier a number

clearTimeout( timerId );  // cancels before the execution
alert( timerId );  // same identifier, doesn't become null after cancelling
```




# `setInterval()`

```js
let timerId = setInterval( func|code, [delay], [arg1], [arg2], ...)
```
unlike `setTimeout` it runs the function not only once, but regularly after the given interval of time.
To stop further calls, we should call `clearInterval(timerId)`.

```js
// repeat with interval of 2 seconds
let timerId = setInterval( () => alert('tick'), 2000 );

// stop after 5 seconds
setTimeout( () => { clearInterval(timerId); alert('stop'); }, 5000);
```

In most browsers, including Chrome and Firefox the internal timer continues “ticking” while showing `alert/confirm/prompt`.

So if you run the code above and don’t dismiss the `alert` window for some time, then the next `alert` will be shown immediately as you do it. The actual interval between alerts will be shorter than 2 seconds.


# ## [Nested setTimeout](https://javascript.info/settimeout-setinterval#nested-settimeout) 

```js
let timerId = setTimeout( function tick() {
	alert('tick');
	timerId = setTimeout(tick, 2000);
}, 2000 );
```
The `setTimeout` above schedules the next call right at the end of the current one
The nested `setTimeout` is a more flexible method than `setInterval`. This way the next call may be scheduled differently, depending on the results of the current one.

