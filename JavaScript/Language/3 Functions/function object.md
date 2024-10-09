
functions are objects.

A good way to imagine functions is as callable “action objects”. We can not only call them, but also treat them as objects: add/remove properties, pass by reference etc.

# The "name" property

Function's name is accessible as the 'name' property.
```js
function sayHi() {
	alert( "Hi" );
}

alert(sayHi.name);  // sayHi
```
Object methods have names too.
```js
let user ={
	sayHi() {
		}.
	sayBye: function() {
	}
}

alert( user.sayHi.name);  // sayHi
alert( user.sayBye.name);  // sayBye
```

Name property is empty if the name cannot be figured out.
```js
ler arr = [function() {}];

alert( arr[0].name );  // <empty string>
```


# The "length" property

Another built-in property “length” that returns the number of function parameters.

```js
function f1(a) {}
function f3(a, b) {}
function f3(a, b, ...more) {}

alert( f1.length );  // 1
alert( f2.length );  // 2
alert( f3.length );  // 2   rest parameter not counted
```


https://javascript.info/function-object



https://javascript.info/new-function

## The `new Function` syntax
The major difference from other ways we’ve seen is that the function is created literally from a string, that is passed at run time.

All previous declarations required us, programmers, to write the function code in the script.
```js
let func = new Function ([arg1, arg2, ...argN], functionBody );
```

```js
let sum = new Function('a', 'b', 'return a + b');

alert( sum(1, 2) ); // 3
```

a function without arguments
```js
let sayHi = new Function('alert("Hello")');

sayHi();   // Hello
```

 `new Function` allows to turn any string into a function. For example, we can receive a new function from a server and then execute it:
```js
let str = ... code from a server dynamically ...

let func = new Function(str);
func();
```


# Closure
[[4 return, call stack, recursion#Closure ???]]

 [Closure](https://javascript.info/new-function#closure)

Usually, a function remembers where it was born in the special property `[[Environment]]`. It references the Lexical Environment from where it’s created (we covered that in the chapter [Variable scope, closure](https://javascript.info/closure)).

But when a function is created using `new Function`, its `[[Environment]]` is set to reference not the current Lexical Environment, but the global one.

So, such function doesn’t have access to outer variables, only to the global ones.

```js
sunction getFunc() {
	let value = "test";

	let func = new Function('alert(value)');

	return func;
}

getFunc()  // error: value is not defined
```
