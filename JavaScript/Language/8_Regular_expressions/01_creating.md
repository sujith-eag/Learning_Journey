
regular expressions. Regular
expressions are a way to describe patterns in string data. They form a small,
separate language that is part of JavaScript and many other languages and
systems.
Regular expressions are both terribly awkward and extremely useful. Their
syntax is cryptic, and the programming interface JavaScript provides for them
is clumsy. But they are a powerful tool for inspecting and processing strings.
Properly understanding regular expressions will make you a more effective pro-
grammer.



### Creating a regular expression

A regular expression is a type of object. It can be either constructed with
the RegExp constructor or written as a literal value by enclosing a pattern in
forward slash (/) characters.

```js
let re1 = new RegExp("abc");

let re2 = /abc/;
```

Both of those regular expression objects represent the same pattern: an a
character followed by a b followed by a c.
When using the RegExp constructor, the pattern is written as a normal string,
so the usual rules apply for backslashes.
The second notation, where the pattern appears between slash characters,
treats backslashes somewhat differently. First, since a forward slash ends the
pattern, we need to put a backslash before any forward slash that we want
to be part of the pattern.

Backslashes tat aren't part of a special character code (like `\n`) will be preserved.
rather than ignored as they are
in strings, and change the meaning of the pattern. Some characters, such as
question marks and plus signs, have special meanings in regular expressions and
must be preceded by a backslash if they are meant to represent the character
itself.
`let aPlus = /A\+/;`


### Testing for matches

Regular expression objects have a number of methods. The simplest one is
test. If you pass it a string, it will return a Boolean telling you whether the
string contains a match of the pattern in the expression.
```js
console.log(/abc/.test("abcde"));
// → true
console.log(/abc/.test("abxde"));
// → false
```
A regular expression consisting of only nonspecial characters simply represents
that sequence of characters. If abc occurs anywhere in the string we are testing
against (not just at the start), test will return true.


___

Regular expressions are objects that represent patterns in strings. They use
their own language to express these patterns.

```
/abc/  sequence of characters
/[abc]/   Any character from a set of characters
/[^abc]/  Any character not in a set of characters
/[0-9]/ Any character in a range of characters

/x+/
One or more occurrences of the pattern x
/x+?/
One or more occurrences, nongreedy
/x*/
Zero or more occurrences
/x?/
Zero or one occurrence
/x{2,4}/ Two to four occurrences
/(abc)/
A group
/a|b|c/
Any one of several patterns
Any digit character
/\d/
/\w/
An alphanumeric character (“word character”)
/\s/
Any whitespace character
/./
Any character except newlines
/\p{L}/u Any letter character
Start of input
/^/
/$/
End of input
/(?=a)/
A look-ahead test
```



A regular expression has a method test to test whether a given string
matches it. It also has a method exec that, when a match is found, returns
an array containing all matched groups. Such an array has an index property
that indicates where the match started.
Strings have a match method to match them against a regular expression
and a search method to search for one, returning only the starting position
of the match. Their replace method can replace matches of a pattern with a
replacement string or function.
Regular expressions can have options, which are written after the closing
slash. The i option makes the match case insensitive. The g option makes
the expression global, which, among other things, causes the replace method
to replace all instances instead of just the first. The y option makes it sticky,
which means that it will not search ahead and skip part of the string when
looking for a match. The u option turns on Unicode mode, which enables \p
syntax and fixes a number of problems around the handling of characters that
take up two code units.

