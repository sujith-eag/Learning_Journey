
## Data Types and Operators

Describe Arithmetic Operators, Assignment Operators, and Comparison Operators with example.

Describe Arithmetic Operators, Assignment Operators, Comparison Operators, Logical Operators and Bitwise Operators in detail with examples.

List the operators supported in Python? Describe specifically about identity and membership operator with a suitable example?

Write a program to display only those numbers from a list that satisfy the following conditions
*  The number must be divisible by five.
* If the number is greater than 100, then skip it and move to the next number.
* If the number is greater than 600, then stop the loop.

Examine each of the following expressions. Predict what the result would be? Explain what the type is for each expression. If an expression is illegal, explain why?
```
i. 10 / 5
ii. 5 / 10
iii. 5.0 / 10
iv. 10 % 4 + 8 / 4
v. 3 ** 10 / 3.
```

#### Describe logical operators and relational operators in python with suitable examples.

An **operator** is a symbol that performs an operation on one or more operands (variables or values).

Logical operators are used to combine conditional statements. They are commonly used in `if` statements to handle multiple conditions.

Operators: `and`, `or`, `not`
- `and`: Returns `True` if both operands are `True`
- `or`: Returns `True` if at least one operand is `True`
- `not`: Reverses the boolean value (returns `True` if the operand is `False`, and vice versa)
```python
x = True
y = False
print(x and y)  # False
print(x or y)   # True
print(not x)    # False
```

Relational (or comparison) operators are used to compare two values. They return a boolean value (`True` or `False`). Operators: `>`, `<`, `==`, `!=`, `<=`, `>=`

- **`>`**: Greater than
- **`<`**: Less than
- **`==`**: Equal to
- **`!=`**: Not equal to
- **`<=`**: Less than or equal to
- **`>=`**: Greater than or equal to

```python
x = 10
y = 20
print(x < y)  # True
print(x == y) # False
print(x != y) # True
```

Relational operators can also be chained. If any condition is `False`, the result will be `False`.

```python
# Example of chaining:
print(5 < 10 < 20)  # True
print(10 < 5 < 20)  # False
```


#### Describe membership operator and identity operator in python with suitable examples.

Membership operators are used to check if a value is present in a sequence (like a string, list, tuple, etc.).

Operators: `in`, `not in`
- `in`: Returns `True` if the value is found in the sequence
- `not in`: Returns `True` if the value is not found in the sequence
```python
fruits = ['apple', 'banana', 'orange']
print('apple' in fruits)    # True
print('grapes' not in fruits)  # True
```

Identity operators are used to compare the memory locations of two objects. These operators help check if two variables point to the same object in memory.

Operators: `is`, `is not`
- `is`: Returns `True` if both operands refer to the same object in memory
- `is not`: Returns `True` if both operands do not refer to the same object

```python
x = [1, 2, 3]
y = [1, 2, 3]
z = x
print(x is y)    # False (different objects in memory)
print(x is z)    # True (same object in memory)
```


___

## Python Programs

Develop a Python program to find roots of a quadratic equation with necessary validation.

Develop a python program to sum the digits of a given number.

Develop a python program to find the sum of even numbers and odd numbers in the given list.

Implement a Python Program to reverse a number and also find the number of digits and Sum of digits in the reversed number. Prompt the user for input.

Design a program to print the mid number (which is between min and max) out of three input numbers

Design a Python program to find the average of best two test scores out of three test scores taken as input.

How do you terminate a loop? Write a Python program to count the palindrome words in a line of text.

Design a simple calculator with different mathematical operations using python script.

Using for loop, print of table of Celsius/Fahrenheit equivalences. Let c be the Celsius temperatures, ranging from 0 to 100. For each value of c, print the corresponding Fahrenheit temperature.

Develop a Python program that will accept, as input, a series of names and salaries. Use the name ‘End’ to mark the end of the sequence of values. After the values have been entered, print the average salary and the names and salaries of those individuals with the highest and lowest salaries.

Develop a script to read n values into a list. Separate the numbers in the list into two new lists, first contains all prime numbers and second contains all non-prime numbers.

___

## Control Flow and Conditionals

Write a program to count the total number of digits and sum of digits in a number using a while loop.

#### Write a python script to demonstrate `if..elif...else` statement in python.

`if...elif...else` are the primary structures for controlling the flow of execution based on conditions.

`if`, `elif`, `else` – Conditional execution of code blocks based on boolean expressions. Python checks each condition in order, and once one condition is true, it skips the rest:

```python
x, y = 3, 4

if x < y:
    print("x is less than y")
elif x > y:
    print("x is greater than y")
else:
    print("x is equal to y")
```

```python
x = 3

if x == 1:
    y = f1(x)
elif x == 2:
    y = f2(x)
elif x == 3:
    y = f3(x)
else:
    y = f4(x)
```

```python
name = input("What is your name? ")

if name == "Harry" or name == "Hermione" or name == "Ron":
    print("Gryffindor")
elif name == "Draco":
    print("Slytherin")
else:
    print("Who?")
```


___

## Loops , break, continue, pass


Demonstrate the usage of pass, continue and break with the help of appropriate example.

Illustrate break, continue and pass statements in Python.

Describe the purpose and usage of Break, Continue and Pass in Python.

In what situations, break and continue statements were used? Discuss with examples.

Illustrate conditions and looping statements in python with suitable examples.

Illustrate the different types of iterative statements available in Python.


What is the output of the following code segments? Explain the causes.
```
i) 
for letter in 'Python':
if letter == 'h':
break
print 'Current Letter :', letter

ii) 
for letter in'Python':
if letter =='h':
continue
print'Current Letter :', letter

iii) 
for letter in'Python':
if letter =='h':
pass
print'This is pass block'
print'Current Letter :', letter
```

#### Demonstrate the usage of pass, break and continue statement in python using suitable examples.

Explain the significance of break, continue and pass with suitable example.

- `break` – Exits the loop immediately.
- `continue` – Skips the rest of the current loop iteration and moves to the next iteration.
- `pass` – Does nothing; used as a placeholder.

```python
prompt = "\nEnter the city you have visited:"
prompt += "\nUse 'quit' to exit. "

while True:
    city = input(prompt)
    if city == "quit":
        break  # Exits when 'quit' is entered
    else:
        print(f"\n{city.title()} is lovely")
```

```python
number = 0

while number < 10:
    number += 1
    if number % 2 == 0:  # Skips even numbers
        continue
    else:
        print(number)  # Prints only odd numbers
```


#### Give the syntax of range() function and discuss its importance. Write a python script to demonstrate for loop statement with range() function.

The `range()` function generates a sequence of numbers, commonly used for looping or generating lists with specific patterns.

- `range(j)` Starts from `0` and ends before `j`. This is equivalent to `range(0, j)`.
```python
range(j)
# Like slice(:j), starts from 0, ends at j-1
```

- `range(i, j)` Generates a sequence of numbers starting from `i` and ending before `j`.
```python
range(i, j)
# Produces the sequence: i, i+1, ..., j-1
```

- `range(i, j, k)`  
Adds an optional third argument `k` for defining the step increment, useful for sequences with a specific pattern, like arithmetic progressions (AP).
```python
range(i, j, k)
# Produces: i, i+k, i+2k, ..., i+nk
```

```python
def factors(n):
	flist = []
	for i in range(1, n + 1):
		if n % i == 0:
			flist.append(i)  
			# Or flist = flist + [i]
	return flist
```


#### Demonstrate the usage of while statement in python. Write a python script to demonstrate while concept to add 5 numbers.

```python
list_1 = [2,4,6,8,10]
number = 0
total = 0
while number < 5:
	total += list[number]    
    number += 1

print(total)
```



Develop a python program that reads two integer values n and m from the user, then produces a box that is n wide and m deep, such as the following:
Enter a width: 5
Enter a height: 4
```

@@@@@
@    @
@    @
@@@@@
```


Develop a python program that takes two positive integers m and n, and then produces a box of mXn dimension as shown below.
Enter height: 4
Enter width: 5
```
*****
*    *
*    *
*    *
*    *
*****
```

Write a program using a while loop that asks the user for a number, and prints a countdown from that number to zero.


Develop a python program that takes two positive integers m and n, and then produces a box of mXn dimension as shown below.
Enter height: 4
Enter width: 5
```
*****
*    *
*    *
*****
```


Develop a program to print the sum of n natural numbers.



___







What are identical objects and equivalent objects? Give examples.

What are identical objects and equivalent objects? Give examples.


Explain the usage of chr() and ord() functions. Develop a script to read a string and convert all uppercase letters to lowercase and vice versa using chr() and ord() functions.

Explain what ord() and chr() function is used for. Using the same, Write a function that takes a string input and converts all uppercase letters to lowercase and vise versa.
Sample input: I love PyTHon
Sample output: i LOVE pYthON.

___
