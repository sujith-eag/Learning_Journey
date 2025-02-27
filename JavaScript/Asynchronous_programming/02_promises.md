
A slightly different way to build an asynchronous program is to have asyn-
chronous functions return an object that represents its (future) result instead
of passing around callback functions. This way such functions actually return
something meaningful, and the shape of the program more closely resembles
that of synchronous programs.



___

This is what the standard class Promise is for. A promise is a receipt repre-
senting a value that may not be available yet. It provides a then method that
allows you to register a function that should be called when the action it is
waiting for finishes. When the promise is resolved, meaning its value becomes
available, such functions (there can be multiple) are called with the result value.
It is possible to call then on a promise that has already resolved—your function
will still be called.


Generally, it is useful to think of promises as a device that lets code ignore the
question of when a value is going to arrive. A normal value has to actually
exist before we can reference it. A promised value is a value that might already
be there or might appear at some point in the future. Computations defined
in terms of promises, by wiring them together with then calls, are executed
asynchronously as their inputs become available.

___

The easiest way to create a promise is by calling Promise.resolve. This
function ensures that the value you give it is wrapped in a promise. If it’s
already a promise, it is simply returned—otherwise, you get a new promise
that immediately resolves with your value as its result.
```js
let fifteen = Promise.resolve(15);
fifteen.then(value => console.log(`Got ${value}`));
// → Got 15
```

___
To create a promise that does not immediately resolve, you can use Promise
as a constructor. It has a somewhat odd interface—the constructor expects a
function as argument, which it immediately calls, passing it a function that it
can use to resolve the promise.
This is how you could create a promise-based interface for the readTextFile
function:
```js
function textFile(filename) {
return new Promise(resolve => {
readTextFile(filename, text => resolve(text));
});
}
textFile("plans.txt").then(console.log);
```
this asynchronous function returns a meaningful value—a promise
to give you the content of the file at some point in the future.

___

A useful thing about the then method is that it itself returns another promise
that resolves to the value returned by the callback function or, if that function
returns a promise, to the value that promise resolves to. Thus, you can “chain”
multiple calls to then together to set up a sequence of asynchronous actions.
This function, which reads a file full of filenames, and returns the content of
a random file in that list, shows this kind of asynchronous promise pipeline.
function randomFile(listFile) {
return textFile(listFile)
.then(content => content.trim().split("\n"))
.then(ls => ls[Math.floor(Math.random() * ls.length)])
.then(filename => textFile(filename));
}
The function returns the result of this chain of then calls. The initial promise
fetches the list of files as a string. The first then call transforms that string
into an array of lines, producing a new promise. The second then call picks a
random line from that, producing a third promise that yields a single filename.
The final then call reads this file, so that the result of the function as a whole
is a promise that returns the content of a random file.
In this code, the functions used in the first two then calls return a regular
value, which will immediately be passed into the promise returned by then
when the function returns. The last one returns a promise (textFile(filename
)), making it an actual asynchronous step.
It would have also been possible to do all these steps inside a single then
callback, since only the last step is actually asynchronous.

___

