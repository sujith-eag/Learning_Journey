If the language is not going to do much to help us find mistakes, we’ll have to
find them the hard way: by running the program and seeing whether it does
the right thing.
Doing this by hand, again and again, is a really bad idea. Not only is
it annoying, it also tends to be ineffective since it takes too much time to
exhaustively test everything every time you make a change.


___

Writing tests is a bit more work than testing manually, but once
you’ve done it, you gain a kind of superpower: it takes you only a few seconds
to verify that your program still behaves properly in all the situations you
wrote tests for. When you break something, you’ll immediately notice, rather
than randomly running into it at some later time.

Tests usually take the form of little labeled programs that verify some aspect
of your code.



there exist pieces of software that help you build and run collections
of tests (test suites) by providing a language (in the form of functions and
methods) suited to expressing tests and by outputting informative information
when a test fails. These are usually called test runners.


### Debugging

Once you notice there is something wrong with your program because it mis-
behaves or produces errors, the next step is to figure out what the problem
is.


Putting a few strategic console.log calls into the program is a good way to
get additional information about what the program is doing.


An alternative to using console.log to peek into the program’s behavior is to
use the debugger capabilities of your browser. Browsers come with the ability
to set a breakpoint on a specific line of your code. When the execution of the
program reaches a line with a breakpoint, it is paused, and you can inspect the
values of bindings at that point.

Another way to set a breakpoint is to include a debugger statement (con-
sisting of simply that keyword) in your program. If the developer tools of
your browser are active, the program will pause whenever it reaches such a
statement.


___

### Exceptions


When a function cannot proceed normally, what we would often like to do is
just stop what we are doing and immediately jump to a place that knows how
to handle the problem. This is what exception handling does.
Exceptions are a mechanism that makes it possible for code that runs into
a problem to raise (or throw) an exception. An exception can be any value.
Raising one somewhat resembles a super-charged return from a function: it
jumps out of not just the current function but also its callers, all the way down
to the first call that started the current execution. This is called unwinding
the stack.


If exceptions always zoomed right down to the bottom of the stack, they
would not be of much use. They’d just provide a novel way to blow up your
program. Their power lies in the fact that you can set “obstacles” along the
stack to catch the exception as it is zooming down. Once you’ve caught an
exception, you can do something with it to address the problem and then
continue to run the program.


```js
function promptDirection(question) 
{
	let result = prompt(question);
	if (result.toLowerCase() == "left") return "L";
	if (result.toLowerCase() == "right") return "R";
	throw new Error("Invalid direction: " + result);
}
function look() 
{
	if (promptDirection("Which way?") == "L") 
	{
	return "a house";
	} else 
	{
	return "two angry bears";
	}
}

try 
{
	console.log("You see", look());
} 
catch (error) 
{
console.log("Something went wrong: " + error);
}
```

When
the code in the try block causes an exception to be raised, the catch block is
evaluated, with the name in parentheses bound to the exception value. After
the catch block finishes—or if the try block finishes without problems—the
program proceeds beneath the entire try/catch statement.


In this case, we used the Error constructor to create our exception value.
This is a standard JavaScript constructor that creates an object with a message
property. Instances of Error also gather information about the call stack
that existed when the exception was created, a so-called stack trace. This
information is stored in the stack property and can be helpful when trying
to debug a problem: it tells us the function where the problem occurred and
which functions made the failing call.


there is another feature that try state-
ments have. They may be followed by a finally block either instead of or in
addition to a catch block. A finally block says “no matter what happens, run
this code after trying to run the code in the try block.”


```js
function transfer(from, amount) {
if (accounts[from] < amount) return;
let progress = 0;
try {
accounts[from] -= amount;
progress = 1;
accounts[getAccount()] += amount;
progress = 2;
} finally {
if (progress == 1) {
accounts[from] += amount;
}
}
}
```
This version of the function tracks its progress, and if, when leaving, it notices
that it was aborted at a point where it had created an inconsistent program

state, it repairs the damage it did.
Note that even though the finally code is run when an exception is thrown
in the try block, it does not interfere with the exception. After the finally
block runs, the stack continues unwinding.

___


JavaScript (in a rather glaring omission) doesn’t provide direct support for
selectively catching exceptions: either you catch them all or you don’t catch
any. This makes it tempting to assume that the exception you get is the one
you were thinking about when you wrote the catch block.


So we want to catch a specific kind of exception. We can do this by checking
in the catch block whether the exception we got is the one we are interested
in and rethrowing it otherwise.


Assertions
Assertions are checks inside a program that verify that something is the way
it is supposed to be. They are used not to handle situations that can come up
in normal operation but to find programmer mistakes.

___


preferable.
Throwing an exception causes the call stack to be unwound until the next
enclosing try/catch block or until the bottom of the stack. The exception
value will be given to the catch block that catches it, which should verify that
it is actually the expected kind of exception and then do something with it.
To help address the unpredictable control flow caused by exceptions, finally
blocks can be used to ensure that a piece of code always runs when a block
finishes.