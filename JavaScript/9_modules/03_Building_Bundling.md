
Many JavaScript packages aren’t, technically, written in JavaScript. There are
extensions, such as TypeScript, the type checking dialect

Because fetching a single big file tends to be faster than fetching a lot of tiny
ones, web programmers have started using tools that combine their programs
(which they painstakingly split into modules) into a single big file before they
publish it to the Web. Such tools are called bundlers.


Apart from the number of files, the size of the
files also determines how fast they can be transferred over the network. Thus,
the JavaScript community has invented minifiers. These are tools that take
a JavaScript program and make it smaller by automatically removing com-
ments and whitespace, renaming bindings, and replacing pieces of code with
equivalent code that take up less space.




So it is not uncommon for the code that you find in an NPM package or that
runs on a web page to have gone through multiple stages of transformation—
converted from modern JavaScript to historic JavaScript, then combining the
modules into a single file, and minifying the code.

___


### Module Design

Good program design is subjective—there are trade-offs involved, and mat-
ters of taste. The best way to learn the value of well-structured design is to
read or work on a lot of programs and notice what works and what doesn’t.
Don’t assume that a painful mess is “just the way it is”. You can improve the
structure of almost everything by putting more thought into it.



when various packages are using different
data structures to describe similar things, combining them is diﬀicult. There-
fore, if you want to design for composability, find out what data structures
other people are using and, when possible, follow their example.

