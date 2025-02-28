
Expressions are evaluated to produce a value, but statements are
executed to make something happen.

Expressions with side effects, such as assignments and function invocations,
can stand alone as statements, and when used this way are known as expression state‐
ments. A similar category of statements are the declaration statements that declare
new variables and define new functions.

By default, the JavaScript interpreter executes these statements one after another in the
order they are written. Another way to “make something happen” is to alter this default order of execution, and JavaScript has a number of statements or control structures that do just this:

Conditionals
Statements like if and switch that make the JavaScript interpreter execute or
skip other statements depending on the value of an expression

Loops
Statements like while and for that execute other statements repetitively

Jumps
Statements like break, return, and throw that cause the interpreter to jump to
another part of the program.


____

#### Expression Statements

The simplest kinds of statements in JavaScript are expressions that have side effects. Assignment statements are one major category of expression statements.:
```
greeting = "Hello " + name;
i *= 3;
```
The increment and decrement operators, ++ and --, are related to assignment state‐
ments.
Function calls are another major category of expression statements.


### Compound and Empty Statements

a statement block combines multiple statements into a single compound
statement. A statement block is simply a sequence of statements enclosed within curly
braces.

```js
{
	x = Math.PI;
	cx = Math.cos(x);
	console.log("cos(π) = " + cx);
}
```
The primitive statements within the block end in semicolons, but the
block itself does not.


A compound statement allows you to use multiple statements where JavaScript syntax
expects a single statement. The empty statement is the opposite: it allows you to
include no statements where one is expected. The empty statement looks like this:
;
The JavaScript interpreter takes no action when it executes an empty statement. The
empty statement is occasionally useful when you want to create a loop that has an
empty body.

```js
// Initialize an array a
for(let i = 0; i < a.length; a[i++] = 0)   ;
```


Note that the accidental inclusion of a semicolon after the right parenthesis of a for
loop, while loop, or if statement can cause frustrating bugs that are difficult to
detect.
```js
if ((a === 0) || (b === 0)); // This line does nothing...
	o = null;   // and this line is always executed.
```

When you intentionally use the empty statement, it is a good idea to comment your code in a way that makes it clear that you are doing it on purpose.

```js
for(let i = 0; i < a.length; a[i++] = 0) /* empty */ ;
```