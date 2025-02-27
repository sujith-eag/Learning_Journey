
Running JS in Browser Console `Ctrl+shift+I`

Running JS on Node
```js
$ node
Welcome to Node.js v20.17.0.
Type ".help" for more information.
> let x = 2, y =3
undefined
> x+y
5
> (x==2) & (x===2) 
1
> (x===2) && ( y ===3)
true
> (x > 2) && ( y < 3)
false
```

```js
> .help
.break    Sometimes you get stuck, this gets you out
.clear    Alias for .break
.editor   Enter editor mode
.exit     Exit the REPL
.help     Print this help message
.load     Load JS from a file into the REPL session
.save     Save all evaluated commands in this REPL session to a file
```

Or save a file with `.js` extension and run in node `$ node snippet.js`
```js
> .editor
// Entering editor mode (Ctrl+D to finish, Ctrl+C to cancel)
let a = []
a.push(1,2,3);
a.reverse();

[ 3, 2, 1 ]

```

___
If you want to see that same message printed out in the JavaScript console of a web
browser, create a new file named hello.html, and put this text in it:
`<script src="hello.js"></script>`
Then load hello.html into your web browser using a file:// URL like this one:
`file:///Users/username/javascript/hello.html`
Open the developer tools window to see the greeting in the console.


____

## Lexical Structure

The lexical structure of a programming language is the set of elementary rules that
specifies how you write programs in that language. It is the lowest-level syntax of a
language: it specifies what variable names look like, the delimiter characters for com‐
ments, and how one program statement is separated from the next, for example. This
short chapter documents the lexical structure of JavaScript. It covers:
• Case sensitivity, spaces, and line breaks
• Comments
• Literals
• Identifiers and reserved words
• Unicode
• Optional semicolons

____


JavaScript is a case-sensitive language. This means that language keywords, variables,
function names, and other identifiers must always be typed with a consistent capitali‐
zation of letters

JavaScript ignores spaces that appear between tokens in programs. For the most part,
JavaScript also ignores line breaks
Because you can
use spaces and newlines freely in your programs, you can format and indent your
programs in a neat and consistent way that makes the code easy to read and
understand.


#### Comments

```js
// anyting follwing a double slashes is a comment

/* This is also a comment */   // and here is another comment.

/*
* This is a multi-line comment. The extra * characters at the start of
* each line are not a required part of the syntax; they just look cool!
*/
```


#### Literals

Literals

A literal is a data value that appears directly in a program. The following are all
literals:
```js
12      // The number twelve
1.2     // The number one point two
"hello world"    // A string of text
'hi'            // Another string
true           // A Boolean value
false         // The other Boolean value
null         // Absence of an object
```


#### Identifiers

An identifier is simply a name. In JavaScript, identifiers are used to name constants,
variables, properties, functions, and classes and to provide labels for certain loops in
JavaScript code.

Digits are not allowed as the first character.
A JavaScript identifier must begin with a letter, an underscore (_), or
a dollar sign ($).
```js
i
my_variable_name
v13
_dummy
$str
```

#### Reserved Words

“reserved words” cannot be used as regular identifiers as they are part of the JS language.

```js
break case catch class const continue debugger default
delete do else enum export extends false finally for
function if implements import interface in instanceof let
new package private protected public return static super
switch this throw true try typeof var void while with yield
```
When creating a binding produces an unexpected syntax error, check whether you’re trying to define a reserved word.


#### Optional Semicolons

Like many programming languages, JavaScript uses the semicolon (;) to separate statements from one another.

You can usually omit the semicolon between two statements if those statements are written on separate lines.

You can also omit a semicolon at the end of a program or if the next token in the
program is a closing curly brace : }

JavaScript does not treat every line break as a semicolon: it usually treats
line breaks as semicolons only if it can’t parse the code without adding an implicit
semicolon.
```js
let a
a
=
3
console.log(a)

// JS interprets this as

let a; a = 3; console.log(a);


return
true;
// JavaScript assumes you meant:
return; true;
```


you must not insert a line break between return, break, or continue
and the expression that follows the keyword. If you do insert a line break, your code
is likely to fail in a nonobvious way that is difficult to debug.