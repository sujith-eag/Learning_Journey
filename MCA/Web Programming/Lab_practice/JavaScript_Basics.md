##### Question 1
Develop a JavaScript code to reverse a given string using loops.
```js
function reverseString(str) {
	let reversed = '';  

  // Loop through the string in reverse
	for (let i = str.length-1 ; i >= 0 ; i--) {
		reversed += str[i];
	}
	return reversed;  
}
```

```
let inputString = "Hello, World!";
let reversedString = reverseString(inputString);
console.log(reversedString);  
//"!dlroW ,olleH"
```

##### Question 2
Develop a JavaScript code to count the number of vowels using loops and if statement.

```js
function countVowels(str) {
	let count = 0;
	
	for (let i = 0; i < str.length; i++) {
		let char = str[i].toLowerCase();
		switch (char) {
			case 'a':
			case 'e':
			case 'i':
			case 'o':
			case 'u':
				count++;
				break;
			default:
				break;  
        }
	}
	return count;
}
```

```js
function countVowels(str) {
	let vowels = 'aeiouAEIOU';
	let count = 0;  
	
	for (let i = 0; i < str.length; i++) {
		if (vowels.indexOf(str[i]) !== -1) {
			count++;  // Increment if it's a vowel
		}
	}
	return count;
}
```

```
let inputString = "Hello, World!";
let vowelCount = countVowels(inputString);
console.log(vowelCount);  // Output: 3

```

##### Question 3
Develop a JavaScript code to find the largest of 3 numbers using if statement and logical
operators.
```js
function findLargest(a, b, c) {
	if (a >= b && a >= c) {
		return a;
	} else if (b >= a && b >= c) {
		return b;
	} else {
		return c;  
	}
}
```

```
let num1 = 10;
let num2 = 25;
let num3 = 15;

let largest = findLargest(num1, num2, num3);
console.log("The largest number is:", largest);  
// "The largest number is: 25"
```

##### Question 4
Develop a JavaScript code to print even and odd numbers from 1 – 10.
```js
function EvenOdd() {
	for (let i = 1; i <= 10; i++) {
		if (i % 2 === 0) {
			console.log(i + " is even");
		} else {
			console.log(i + " is odd");
		}
	}
}

EvenOdd();
```

##### Question 5
Develop a JavaScript code program that prints the numbers from 1 to 20. However, for
multiples of 3, print "Fizz" instead of the number, for multiples of 5, print "Buzz",
and for numbers that are multiples of both 3 and 5, print "FizzBuzz".

```js
function fizzBuzz() {
	for (let i = 1; i <= 20; i++) {
		if (i % 3 === 0 && i % 5 === 0) {
			console.log("FizzBuzz");
		}
		else if (i % 3 === 0) {
			console.log("Fizz");
		}
		else if (i % 5 === 0) {
			console.log("Buzz");
		}
		else {
			console.log(i);
		}
	}
}

fizzBuzz();
```


___

### JavaScript Strings (Data Sheet 14)

##### Question 1
Declare a string and display it using `innerHTML`.
```html
<body>
    <div id="displayArea"></div>
    
    <script>
        let myString = "A string displayed using innerHTML!";    
        let disArea = document.getElementById("displayArea");
        disArea.innerHTML = myString;
    </script>
</body>
</html>
```

##### Question 2
Display the string containing special characters(quotes) using backslash escape
character.
```html
<body>
    <div id="displayArea"></div>
    
    <script>
        let myString = "She said, \"Hello, how are you?\"";
		let disArea = document.getElementById("displayArea");
        disArea.innerHTML = myString;
    </script>
</body>
</html>
```

##### Question 3
Demonstrate the `slice()` with no parameters, one parameter, two parameters and
negative parameters

Slice is used to extract a portion of string or array.
```js
array.slice(beginIndex, endIndex);
string.slice(beginIndex, endIndex);
```

```js
let str = "Hello, World!";
let result = str.slice();
console.log(result);  
// "Hello, World!"
```

```js
let str = "Hello, World!";
let result = str.slice(7);  // from 7 to the end
console.log(result);  
// "World!"
```

```js
let str = "Hello, World!";
let result = str.slice(0, 5);  // excludes index 5
console.log(result);  
// "Hello"
```

```js
let str = "Hello, World!";
let result = str.slice(-6, -1);  // excluding -1
console.log(result);
// "World"
```

```html
<body>
    <h3>String Slice Examples</h3>
    
    <div id="output"></div>

    <script>
        let str = "Hello, World!";

        let noParams = str.slice();
        let oneParam = str.slice(7);
        let twoParams = str.slice(0, 5);
        let negativeParams = str.slice(-6, -1);

        document.getElementById("output").innerHTML = `
            <p>No parameters: ${noParams}</p>
            <p>One parameter: ${oneParam}</p>
            <p>Two parameters: ${twoParams}</p>
            <p>Negative parameters: ${negativeParams}</p>
        `;
    </script>
</body>
</html>
```

##### Question 4
Demonstrate the `substr()` with no parameters, one parameter, two parameters and
negative parameters

`substr()` method extracts a portion of a string starting from a specified index and for a specified length.
```js
string.substr(startIndex, length);
```

```js
let str = "Hello, World!";
let result = str.substr();
console.log(result);  
// "Hello, World!"
```

```js
let str = "Hello, World!";
let result = str.substr(7); // from 7 to end
console.log(result);  
// "World!"
```

```js
let str = "Hello, World!";
let result = str.substr(7, 3); 
console.log(result);
// "Wor"
```

```js
let str = "Hello, World!";
let result = str.substr(-6, 5);
console.log(result);  
// "World"
```

```js
<body>
    <h3>String Substr Examples</h3>
    <div id="output"></div>

    <script>
        let str = "Hello, World!";
		
		let noParams = str.substr();
        let oneParam = str.substr(7);
        let twoParams = str.substr(0, 5);
        let negativeParams = str.substr(-6, 5);

        document.getElementById("output").innerHTML = `
            <p>No parameters: ${noParams}</p>
            <p>One parameter: ${oneParam}</p>
            <p>Two parameters: ${twoParams}</p>
            <p>Negative parameters: ${negativeParams}</p>
        `;
    </script>
</body>
</html>
```
##### Question 5
Demonstrate the `replace()` and `replaceAll()` methods

```js
string.replace(searchValue, newValue);
string.replaceAll(searchValue, newValue);
```

```js
let str = "Hello, World! Hello again!";

let result = str.replace("Hello", "Hi");
console.log(result);  
// "Hi, World! Hello again!"

let result1 = str.replaceAll("Hello", "Hi");
console.log(result);  
// "Hi, World! Hi again!"
```

____

### JavaScript Arrays (Data Sheet 15)


##### Question 1
Declare an array using literal and print the array elements using for loop.
```html
<body>
    <h3>Array Elements:</h3>

	<div id="output"></div>

    <script>
        let myArray = [10, 20, 30, 40, 50];
        
        let output = '';
        for (let i = 0; i < myArray.length; i++) {
            output += `Element at index ${i} : ${myArray[i]} <br>`;
        }
        
        document.getElementById("output").innerHTML = output;
    </script>
</body>
</html>
```

##### Question 2
Declare an array using new constructor and print the array elements using `forEach()`.
```html
<body>
    <h3>Array Elements:</h3>
    <div id="output"></div>

    <script>
        let myArray = new Array(10, 20, 30, 40, 50);
        let output = '';

        myArray.forEach( element => {
            output += `Element is ${element} <br>`;
        });

        document.getElementById("output").innerHTML = output;
    </script>
</body>
</html>
```

Using a named function instead of Arrow function
```js
let myArray = new Array(10, 20, 30, 40, 50);

myArray.forEach(printElement);

function printElement(element) {
    console.log(`Element is ${element}`);
}
```

##### Question 3
Create an array of numbers and print the Fibonacci series with the help of `forEach()`
method.
```html
<body>
    <h3>Fibonacci Series:</h3>
    <div id="output"></div>

<script>
    function fibonacci(n) {
        if (n <= 1) {
            return n;
        }
        return fibonacci(n - 1) + fibonacci(n - 2);
    }

    let n = 10;
    let fibArray = [];
    for (let i = 0; i < n; i++) {
        fibArray.push(fibonacci(i));
    }
    console.log(fibArray);
</script>

</body>
</html>

```

##### Question 4
Create an array of numbers and print the sum of numbers with the help of `forEach()`
method.
```html
<body>
    <h3>Sum of Numbers:</h3>
    <div id="output"></div>

    <script>
        let numbers = [1, 2, 3, 4, 5];
        let sum = 0;
        
        numbers.forEach( element => {
            sum += element;
        });

		let display = document.getElementById("output");
		display.innerHTML = `The sum of the numbers is: ${sum}`;
    </script>
</body>
```

##### Question 5
Use the `Array.forEach()` method to copy every element from one array to another.
```html
<body>
    <h3>Copying Elements from One Array to Another:</h3>
    <div id="output"></div>

    <script>
        let sourceArray = [10, 20, 30, 40, 50];
        let destinationArray = [];
        
        sourceArray.forEach(element => {
            destinationArray.push(element); 
        });
        
        document.getElementById("output").innerHTML = `Destination Array: [${destinationArray.join(", ")}]`;
    </script>
</body>
```

##### Question 6
Develop a javascript program to demonstrate the concept of arrays and its following
methods i) `join()`, `reverse()`, `sort()` and `concat()`.
```html
<body>
    <h3>Array Methods: join(), reverse(), sort(), and concat()</h3>
    <div id="output"></div>

    <script>
        let numbers = [5, 3, 8, 1, 2];

        let joinedNumbers = numbers.join(", ");
        let reversedNumbers = [...numbers].reverse(); 
        let sortedNumbers = [...numbers].sort((a, b) => a - b);
        
        let moreNumbers = [10, 20, 30];
        let combinedNumbers = numbers.concat(moreNumbers);

        let output = `
            Original Array: [${numbers.join(", ")}] <br>
            After join(): ${joinedNumbers} <br>
            After reverse(): [${reversedNumbers.join(", ")}] <br>
            After sort(): [${sortedNumbers.join(", ")}] <br>
            After concat() with [${moreNumbers.join(", ")}]: [${combinedNumbers.join(", ")}]
        `;
		document.getElementById("output").innerHTML = output;
    </script>
</body>
```


_____
