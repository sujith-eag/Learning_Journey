
There are some things that JavaScript does complain about. Writing a pro-
gram that does not follow the language’s grammar will immediately make the
computer complain. Other things, such as calling something that’s not a func-
tion or looking up a property on an undefined value, will cause an error to be
reported when the program tries to perform the action.

But often, your nonsense computation will merely produce NaN (not a num-
ber) or an undefined value, while the program happily continues, convinced
that it’s doing something meaningful. The mistake will manifest itself only
later, after the bogus value has traveled through several functions. It might
not trigger an error at all but silently cause the program’s output to be wrong.
Finding the source of such problems can be diﬀicult.

The process of finding mistakes—bugs—in programs is called debugging.


## Strict Mode

JavaScript can be made a little stricter by enabling strict mode. This is done by
putting the string "use strict" at the top of a file or a function body.

```js
function canYouSpotTheProblem() 
{
	"use strict";
	for (counter = 0; counter < 10; counter++)
	{
		console.log("Happy happy");
	}
}

canYouSpotTheProblem();
// -> ReferenceError: counter is not defined
```

Normally, when you forget to put let in front of your binding, as with counter
in the example, JavaScript quietly creates a global binding and uses that. In
strict mode, an error is reported instead.


___
Another change in strict mode is that the this binding holds the value
undefined in functions that are not called as methods. When making such
a call outside of strict mode, this refers to the global scope object, which is
an object whose properties are the global bindings. So if you accidentally call
a method or constructor incorrectly in strict mode, JavaScript will produce
an error as soon as it tries to read something from this, rather than happily
writing to the global scope.


```js
function Person(name) { this.name = name; }
let ferinand = Person("Ferdinand");

console.log(name);
// Ferdinand
```
So the bogus call to Person succeeded but returned an undefined value and
created the global binding name. In strict mode, the result is different.

```js
"use strict"
function Person(name) { this.name = name; }
let ferinand = Person("Ferdinand");
// forgot new

// -> TypeeError: cannot set property 'name' of undefined
```


Strict mode does a few more things. It disallows giving a function multiple
parameters with the same name and removes certain problematic language
features entirely (such as the with statement)



### Types 

A lot of
mistakes come from being confused about the kind of value that goes into or
comes out of a function. If you have that information written down, you’re less
likely to get confused.

Some languages want to know the types of all your bindings and expressions
before even running a program. They will tell you right away when a type
is used in an inconsistent way. 


JavaScript considers types only when actually
running the program, and even there often tries to implicitly convert values to
the type it expects, so it’s not much help.

There
are several JavaScript dialects that add types to the language and check them.
The most popular one is called TypeScript. If you are interested in adding
more rigor to your programs, I recommend you give it a try.

In this book, we’ll continue using raw, dangerous, untyped JavaScript code.

