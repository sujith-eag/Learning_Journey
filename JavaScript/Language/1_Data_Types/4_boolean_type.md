
### boolean

Has only two values `true` and `false` for storing yes or no, right or wrong.
```js
let nameFieldChecked = true;
let ageDieldChecked = false;
```

##### Comparisons `==  !=  >=  <= `

Boolean values come as a result of comparisons

```js
console.log(3>2);   //true
console.log(2>3);   //false
```

***String Comparison***
```js
alert( 'z' > 'A')  // true
alert( 'Glow' > 'Glee' )  // true
alert( 'Bee' > 'Be' )  // true
alert("Aardvark" < "Zoroaster") //true
```

When comparing strings `js` goes from left to right comparing each characters Unicode code one by one. 
So capital is more than small, non-alphabetical characters also included.
The first difference it returns a value. 
Longer ones are greater than short ones.

_____
[[Type_Conversions]]
____

### Strict Comparison  `===`   `!==`

When we do not want any type conversion, there are two more operators. regular check `==` cannot differentiate `0` from `fasle`.
```js
// 0 is seen as false by ==
alert( 0 == false); // true
alert("" == false); // true
// empty string is converted to 0, which is false again

alert("" === false); // false
alert( 0 === false); // false
```
These three character comparison can be used defensively to prevent unexpected type conversion.

___

### Comparison with `null` & `undefined`

When `null` or `undefined` occurs on either side of the operator, it produces true only if both sides are one of `null` or `undefined`
```js
alert(null == undefined);    // true
alert(null === undefined);    // false

alert(null == 0);            // false
```

Useful to test if a value has a real value instead of `null` or `undefined` by comparing it to `null` with the `==` or `!=` operator.
```js
0 == false  // true
"" == false  // true
```

for math comparisons `> < <= >=` `null/undefined` is converted to numbers:  `null` becomes `0`  , `undefined` becomes `NaN`

