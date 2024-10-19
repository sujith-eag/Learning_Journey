
## Transparent caching

```js
fuction slow(x) {
	// some process
	alert('called with ${x}');
	return x;
}

function chchingDecorator(func) {  // decorator that takes another function
	let cache = new Map();         // and alters its behaviour

	return function(x) {
		if (cache.has(x)) {       // if there is such a key in cache
			return cache.get(x);  // read the result from it
			}
			
		let result = func(x);   // otherwise call the function
		
		cache.set(x, result);  // and cache the result   
		return result;  
		};
}

slow = cachingDecorator(slow);

alert( slow(1));         // slow(1) is cached and the result is returned
alert( "Again: " + slow(1) );  // slow(1) results returned from cache


alert( slow(2));         // slow(2) is cached and the result is returned
alert( "Again: " + slow(2) );  // slow(2) results returned from cache
```

`cachingDecorator` is called for any function and it will return the caching wrapper.
The result of `cachingDecorator(func)` is a wrapper: `function(x`) that wraps the call of the `func(x)` into caching logic.

The caching decorator is not suited to work with object methods.

# `func.call()`

```js
func.call(context, arg1, arg2, ...)
```

It allows to call a function explicitly setting `this`.
```js
func(1, 2, 3);
func.call(obj, 1, 2, 3);
```
both call `func` with argument, but `func.call` sets `this` to `obj`. 

```js
function sayHi() {
	alert(this.name);
}

let user = { name: "John" };
let admin = { name: "Admin" };

// using call to pass different objects as 'this'
sayHi.call( user );  // John
sayHi.call( admin );  // Admin
```
`sayHi.call(user)` runs `sayHi` providing `this = user` and next one sets `this = admin`


```js
function say(phrase) {
	alert(this.name + ": " + phrase);
}

let user = { name: "John" };

say.call( user, "Hello" );  // John: Hello
// user becomes this, and "Hello" becomes the first argument
```

???????
https://javascript.info/call-apply-decorators

`func.apply(context, args)`

https://javascript.info/bind
`func.bind(user)`
?????
