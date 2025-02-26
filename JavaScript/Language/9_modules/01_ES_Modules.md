
A module is a piece of program
that specifies which other pieces it relies on and which functionality it provides
for other modules to use (its interface).
Module interfaces have a lot in common with object interfaces,


A good module system also requires modules to specify which code they
use from other modules. These relations are called dependencies. If module
A uses functionality from module B, it is said to depend on it.

When these are clearly specified in the module itself, they can be used to figure out which
other modules need to be present to be able to use a given module and to
automatically load dependencies.

___

### ES Modules

Since ECMAScript 2015, JavaScript supports two different types of pro-
grams. Scripts behave in the old way: their bindings are defined in the global
scope, and they have no way to directly reference other scripts. Modules get
their own separate scope, and support the import and export keywords, which
aren’t available in scripts, to declare their dependencies and interface. This
module system is usually called ES modules

___

A modular program is composed of a number of such modules, wired together via import and export


This example module converts between day names and numbers (as returned
by Date’s getDay method). It defines a constant which is not part of its interface,
and two functions which are. It has no dependencies.

```js
const names = ["Sunday", "Monday", "Tuesday", "Wednesday",
"Thursday", "Friday", "Saturday"];
export function dayName(number) {
return names[number];
}
export function dayNumber(name) {
return names.indexOf(name);
}
```
The export keyword can be put in front of a function, class, or binding definition
to indicate that that binding is part of the module’s interface. This makes it
possible for other modules to use that binding by importing it.


The export keyword can be put in front of a function, class, or binding definition
to indicate that that binding is part of the module’s interface. This makes it
possible for other modules to use that binding by importing it.

```js
import {dayName} from "./dayname.js";

let now = new Date();
console.log(`Today is ${dayName(now.getDay())}`);
// → Today is Monday

```

The import keyword, followed by a list of binding names in braces, makes
bindings from another module available in the current module. Modules are
identified by quoted strings.


___

How such a module name is resolved to an actual program differs by platform.
The browser treats them as Web addresses, whereas Node.js resolves them to
files. To run a module, all the other modules it depends on—and the modules
those depend on—are loaded, and the exported bindings are made available to
the modules that import them.
Import and export declarations cannot appear inside of functions, loops,
or other blocks. They are immediately resolved when the module is loaded,
regardless of how the code in the module executes, and to reflect this they
must appear only in the outer module body.

Imported bindings can be
renamed to give them a new local name using as after their name.

```
import {dayName as nomDeJour} from "./dayname.js";
console.log(nomDeJour(3));
// → Wednesday
```
It is also possible for a module to have a special export named default, which
is often used for modules that only export a single binding. To define a default
export, you write export default before an expression, a function declaration,
or a class declaration.
```
export default ["Winter", "Spring", "Summer", "Autumn"];
```
Such a binding is imported by omitting the braces around the name of the
import.
```
import seasonNames from "./seasonname.js";
```


