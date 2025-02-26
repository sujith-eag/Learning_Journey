
In a synchronous programming model, things happen one at a time. When you
call a function that performs a long-running action, it returns only when the
action has finished and it can return the result. This stops your program for
the time the action takes.
An asynchronous model allows multiple things to happen at the same time.
When you start an action, your program continues to run. When the action
finishes, the program is informed and gets access to the result (for example,
the data read from disk).


to start additional
threads of control. A thread is another running program whose execution may
be interleaved with other programs by the operating system—since most mod-
ern computers contain multiple processors, multiple threads may even run at
the same time, on different processors. A second thread could start the second
request, and then both threads wait for their results to come back, after which
they resynchronize to combine their results.




Another way to describe the difference is that waiting for actions to finish
is implicit in the synchronous model, while it is explicit, under our control, in
the asynchronous one.
Asynchronicity cuts both ways. It makes expressing programs that do not
fit the straight-line model of control easier, but it can also make expressing
programs that do follow a straight line more awkward.


Both prominent JavaScript programming platforms—browsers and Node.js—
make operations that might take a while asynchronous, rather than relying on
threads. Since programming with threads is notoriously hard (understanding
what a program does is much more diﬀicult when it’s doing multiple things at
once), this is generally considered a good thing.


___

### Callbacks

One approach to asynchronous programming is to make functions that need
to wait for something take an extra argument, a callback function. The asyn-
chronous a function starts some process, sets things up so that the callback
function is called when the process finishes, and then returns.

As an example, the setTimeout function, available both in Node.js and in
browsers, waits a given number of milliseconds (a second is a thousand mil-
liseconds) and then calls a function.
```
setTimeout( () => console.log("Tick"), 500);
```

Another example of a common asynchronous operation is reading a file from
a device’s storage. Imagine you have a function readTextFile, which reads a
file’s content as a string and passes it to a callback function
```
readTextFile("shopping_list.txt", content => {
console.log(`Shopping List:\n${content}`);
});
// → Shopping List:
// → Peanut butter
// → Bananas
```


Performing multiple asynchronous actions in a row using callbacks means
that you have to keep passing new functions to handle the continuation of the
computation after the actions. This is what an asynchronous function that
compares two files and produces a boolean indicating whether their content is
the same might look like.
```
function compareFiles(fileA, fileB, callback) {
readTextFile(fileA, contentA => {
readTextFile(fileB, contentB => {
callback(contentA == contentB);
});
});
}
```
This style of programming is workable, but the indentation level increases with
each asynchronous action because you end up in another function.


wrapping asynchronous actions in a loop, can get
awkward.
In a way, asynchronicity is contagious. Any function that calls a function
that works asynchronously must itself be asynchronous, using a callback or
similar mechanism to deliver its result. Calling a callback is somewhat more
involved and error-prone than simply returning a value, so needing to structure
large parts of your program that way is not great.