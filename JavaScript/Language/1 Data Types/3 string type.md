

### strings

Text which are enclosed in ` ' '  " "  `` ` quotes.
```js
let str = "Hello";
let str1 = 'single quotes are ok too';

let phrase = `backticks are fine and can embed another ${str}`;
let combined = `${str}${phrase}`;

alert( `1 + 2 = ${ sum(1, 2) }.`);
```

***Template literals*** `${}`  can embed other values
\`\` are extended functionality quotes. they allow us to embed variables and expressions into a string by wrapping them in `${ }`.
When something is inside `${ }` is a template literal, its result will be computed, converted to a string and included at that position.

```js
`half of 100 is ${100/2}`
`half of 100 is 50`

let name = "john";
console.log( `Hello, ${name}`);
console.log( `the result is ${1+2}`);
```
Single and double quotes cannot do this embedding functionality.
Back-ticks allow a string to span multiple lines.


***escaping character*** means that we do something to make sure they are recognized as text, not part of the code. which is done by putting `\` just before the character. 
Newline can be represented by `backticks \` which is a ***escaping character***.

`\n` represents new line,  `\t` for tab
`\\` ***two back slashes*** are present, they collapse and become a normal Backslash.
```js
First line and\nThis is second line
A newline character is "\n"
A newline character is \"\\n\"

cosnt bigmouth = 'I\'ve got no right to take my place';
```
First and last one is for escaping " " quotes and next two becomes one slash


***Concatenate***
`+` operator can be used to *concatenate strings*
```js
let name = "con" + "cat" + "e" + "nate"
```

If any one of the operands is a string, then the other will also be converted to a string.
```js
alert ( '1' + 2);  // 12
alert ( 2 + "1");  // 21

// tests one after the other from left to right
alert ( 2 + 1+ "1");  // 31 not 211
alert ( "2" + 1+ 1);  // 211 not 22
```

All other math operators try to convert string to number and do the operation but not `+`

`String()` function converts its argument to string.