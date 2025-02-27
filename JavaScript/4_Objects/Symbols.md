
Symbols were introduced in ES6 to serve as non-string property names. 

Property names in objecr are typically (and until ES6, were exclusively) strings. But in ES6 and later, Symbols can also serve this purpose:

```js
> let strname = "string name";
> typeof strname
'string'

> let symbname = Symbol("Propane");
> typeof(symbname)
'symbol'

> let o = {};    // create a new object
> o[strname] = 1;   // name with string name
1
> o[symbname] = 2;   // name with symbol name
2
> o[symbname]   // acessing value
2
> o    // object
{ 'string name': 1, [Symbol(Propane)]: 2 }
```



The Symbol() function takes an optional string argument and returns a unique Symbol value. If you supply a string argument, that string will be included in the output of the Symbol’s toString() method. Note, however, that calling Symbol() twice with the same string produces two completely different Symbol values.

```js
> let s = Symbol();
undefined
> s.toString()
'Symbol()'
> typeof(s)
'symbol'

> let p = Symbol("sym_x");
undefined
> p.toString()
'Symbol(sym_x)'

> let q = Symbol("sym_x");
undefined
> q.toString()
'Symbol(sym_x)'

```


if you call Symbol() to obtain a Sym‐
bol value, you can safely use that value as a property name to add a new property to
an object and do not need to worry that you might be overwriting an existing prop‐
erty with the same name. Similarly, if you use symbolic property names and do not
share those symbols, you can be confident that other modules of code in your pro‐
gram will not accidentally overwrite your properties.



`Symbol.iterator` is a Symbol value that can be used as a method name to make an object iterable.



JavaScript defines a global Symbol registry. The
Symbol.for() function takes a string argument and returns a Symbol value that is
associated with the string you pass. If no Symbol is already associated with that string,
then a new one is created and returned; otherwise, the already existing Symbol is
returned. That is, the Symbol.for() function is completely different than the Sym
bol() function: Symbol() never returns the same value twice, but Symbol.for()
always returns the same value when called with the same string. The string passed to
Symbol.for() appears in the output of toString() for the returned Symbol, and it
can also be retrieved by calling Symbol.keyFor() on the returned Symbol.

```js
> let s = Symbol.for("shared");
undefined
> let t = Symbol.for("shared");
undefined

> s === t
true
> Symbol.keyFor(t)
'shared'
```

```js
> let p = Symbol("notshare");
undefined
> let q = Symbol("notshate");
undefined

> p === q
false
> Symbol.keyFor(p)
undefined
> Symbol.keyFor(q)
undefined

```