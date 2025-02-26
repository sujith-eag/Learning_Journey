
One of the most pressing problems with the callback style of asynchronous
programming is that it makes it extremely diﬀicult to make sure failures are
properly reported to the callbacks.


Regular JavaScript computations can fail by throwing an exception. Asyn-
chronous computations often need something like that. A network request
may fail, a file may not exist, or some code that is part of the asynchronous
computation may throw an exception.


___
Promises make this easier. They can be either resolved (the action finished
successfully) or rejected (it failed).


if any element in a chain of asynchronous actions fails, the outcome of the
whole chain is marked as rejected, and no success handlers are called beyond
the point where it failed.


Much like resolving a promise provides a value, rejecting one also provides
one, usually called the reason of the rejection.