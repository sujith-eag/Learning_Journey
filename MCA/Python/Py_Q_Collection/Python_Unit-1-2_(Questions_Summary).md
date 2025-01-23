### **String Operations**

1. Mention the data types in Python with an example for each.
2. Demonstrate slicing on strings. Also, explain the use of `join()` and `split()` string methods with examples.
3. What is a string? Discuss the different ways of representing a string in Python.
4. Write a Python program to count the frequency of words in a string using a dictionary.
5. Write a Python function to return the number of palindrome words in a line of text.
6. Write a Python function to check if a string is a palindrome.
    - The function should take "MADAM" as the default argument.
    - It should return a Boolean value.
7. Predict the output of the following and justify your answer:
```python
# (i)
s = "Vishweswaraiah"
print(s[4:])
print(s[:5])

# (ii)
str1 = "Bangalore"
str1[1] = "e"
str1[6] = str1[8] = "u"
print(str1)

# (iii)
a = -45
print(--a)

# (iv)
a, b, c = True, False, False
if a or b and c:
	print("MSRIT")
else:
	print("RNSIT")
```

8. Write a Python script to generate the third-person singular form of verbs based on the following rules:
    - If the verb ends in `y`, remove it and add `ies`.
    - If the verb ends in `o`, `ch`, `s`, `sh`, `x`, or `z`, add `es`.
    - Otherwise, add `s`.

#### **String Methods**

9. **Explain the usage of the following methods with examples:**
    - **(i)** `extend()`
    - **(ii)** `pop()`
    - **(iii)** `sort()`
    - **(iv)** `split()`
    - **(v)** `join()`

10. Explain the use of `ord()` and `chr()` functions. Write a function that converts all uppercase letters to lowercase and vice versa in a given string.  
    Example Input: `I love PyTHon`  
    Example Output: `i LOVE pYthON`

---

### **Data Structures**

#### **Lists, Tuples, and Sets**

1. Compare and contrast lists, tuples, and sets.
2. List and describe any five methods on tuples.
3. Create a list of even numbers from 1 to 10 using both a loop and the filter method.
4. Demonstrate any four functions of lists with examples.
5.  Write a Python program to print unique elements from a list.

#### **Dictionaries**

5. How do you create and access dictionaries in Python? Explain the operations `len()`, `copy()`, `clear()`, and `items()` on dictionaries.
6. Write a Python program to count the occurrences of a letter in a string using dictionaries.
7. Develop a Python program to print the intersection of two lists (without using list comprehension or sets).
8. Implement a telephone directory using dictionaries.
9. Demonstrate any three functions of dictionaries in Python with examples.
10. Write a Python program to create a dictionary from a list where keys are elements and values are their frequencies.

#### **Data Structure Operations**

10. Store the following data in a list, a tuple, and a dictionary:
```
India    91
USA      1
UK       41
Japan    9
```

11. Consider the list `scores = [5, 4, 7, 3, 6, 2, 1]` and write Python instructions to perform the following operations:
    - **(i)** Insert an element `9` at the beginning of the list.
    - **(ii)** Insert an element `8` at index position `3` of the list.
    - **(iii)** Delete an element at the end of the list.
    - **(iv)** Delete an element at index position `3`.

#### **Data Structure Properties**

12. What do you mean by mutable and immutable data structures? Explain with examples.
13. When you use the `+` operator to concatenate two lists, does it make a copy or a reference of the arguments? Explain with the help of an example.

---

### **Expressions and Evaluations**

#### **Evaluations**

1. Evaluate the results of the following expressions:
- **(i)** `not "True"`
- **(ii)** `-22 % 5`
- **(iii)** `"99" + 1`
- **(iv)** `dir("python")`
- **(v)** `['H', 'He', 'Li'] + 'Be'`
 
2. Examine the following expressions. Predict the result and explain the type of each expression. If an expression is illegal, explain why:
- **(i)** `10 / 5`
- **(ii)** `5 / 10`
- **(iii)** `5.0 / 10`
- **(iv)** `10 % 4 + 8 / 4`
- **(v)** `3 ** 10 / 3`

___
---

### **Control Flow and Logic**

1. Explain the significance of `break`, `continue`, and `pass` with a suitable example.

2. Predict the output of the following code snippets and justify your answers:
```python
i) a = -45
   print(--a)
ii) str1 = 'hello'
	print(str1[-1:])
iii) a = [1, 2, 3, 4, 5, 6, 7, 8, 9]
	 a[::2] = 10, 30, 50, 50, 90
iv) a, b, c = True, False, False
	if a or b and c:
		print("MSRIT")
	else:
		print("RNSIT")
```

3. Predict the output of the following code snippets and justify your answers:
    ```python
i) 22 < "A"

ii) i = 5
	print("welcome") if i > 5 else print("bye")

iii) [1, 2] in [0, 1, 2, 3]

iv) s = "programming"
	print(s[5:-2])

v) ls = [34, 'hi', -5]
	ls.sort()
```

#### **Scope and Variables**
4. Explain (or Demonstrate) the scope of local and global variables.
5. Explain the significance of the following concepts in Python:
    - Local and global variables
    - DOC strings
    - `map()` and `reduce()` functions

---

#### **LEGB Rule**
6. What is the LEGB rule? Provide examples. Apply the LEGB rule to the following code and explain what is happening. Also, write the output:
```python
a = 7
def fun(b):
	c = 17
	def morefun(d):
		e = 12
		print(a + b + c + d + e)
	morefun(3)
fun(5)
```

#### **Operators**
7. Describe Arithmetic Operators, Assignment Operators, Comparison Operators, Logical Operators, and Bitwise Operators in detail with examples.
#### **Objects and Identicality**
8. What are identical objects and equivalent objects? Provide examples.
#### **Implementation and User Input**
9. Implement a Python program to reverse a number, count the number of digits, and calculate the sum of the digits in the reversed number. Prompt the user for input.

---

### **Loops and Iterative Statements**

#### **Iterative Structures**
1. Illustrate the different types of iterative statements available in Python.
2. Write a program to count the total number of digits and the sum of digits in a number using a while loop.
3. Develop a Python program to find the sum of even numbers and odd numbers in a given list.
4. Develop a Python program to extract the indices of even elements from a list.

#### **For Loop Applications**
5. Use a `for` loop to perform the following tasks (give examples for):
    - Process characters in a string
    - Display values and keys of a dictionary
    - Loop over a list of lists
6. Using a `for` loop, print a table of Celsius/Fahrenheit equivalences. Let `c` be the Celsius temperatures ranging from 0 to 100. For each value of `c`, print the corresponding Fahrenheit temperature.


#### **Pattern Generation**
8. Define a function that takes a positive integer `n` and produces `n` lines of output in the following pattern:  
```
+
+ +
+ + +
+ + + +
+ + + + +
```  
Is it possible to get the same output using a single loop? Justify.

#### **Specialized Loops**
9. Write a program to display only those numbers from a list that satisfy the following conditions:  
    - The number must be divisible by five.  
    - If the number is greater than 150, skip it and move to the next number.  
    - If the number is greater than 500, stop the loop.

#### **Creative Loops**
10. **Develop a Python program that reads two integer values, `n` and `m`, from the user and produces a box of size `n x m`.**
    Example:
```python
Enter a width: 5
Enter a height: 4
@@@@@
@   @
@   @
@@@@@
```

11. What is the output of the following code segments? Explain the causes:  
```python
for letter in 'Python':     
	if letter == 'h':  
		break  
	print('Current Letter:', letter)
```  

```python
for letter in 'Python':  
	if letter == 'h':  
		continue  
	print('Current Letter:', letter)
```  

```python
for letter in 'Python':  
	if letter == 'h':  
		pass  
	print('This is pass block')  
	print('Current Letter:', letter)
    ```

---
___

### **Functions and Recursion**

#### **Functions and Arguments**

1. Develop a Python function to calculate the sum and product of two arguments and return them.
2. Write a Python function that accepts a sentence containing alphanumeric characters and calculates the number of digits, uppercase, and lowercase letters. Return the calculated values.
3. Write a function to find the factorial of a number using functional programming.
4. Exemplify the various types of formal arguments in Python.
5. Differentiate between keyword arguments, required arguments, and variable-length arguments with examples.
6. Discuss the following ways of passing parameters to functions with examples:
    - Keyword-only parameters
    - Variable-length arguments
    - Pass by reference and pass by value

#### **Lambda and Functional Programming**
1. What is a lambda function? What are its characteristics? Provide an example.  
2. Using the `filter` and `lambda` functions, produce the following outputs from a list created using `range(1, 11)`:  
    - A list of even numbers  
    - A list of values divisible by 3  
3. Using the functions `map` and a `lambda` argument, generate the following from a list of values produced by `range(1, 11)`:  
    - A list of squares of the values  
    - A list of cubes of the values  
    - A list where each element is larger by one than the corresponding element in the original list  
4. Write short notes on the following topics:  
    - Mapping  
    - Filtering  
    - List comprehension  
5. Explain filtering and reduction operations with examples.  
6. Illustrate how `reduce` can be used to find the product of all elements in a list.  
7. Write a lambda function for each of the following tasks:  
    - Take one argument and return `True` if it is nonzero. 
    - Take one argument and return `True` if it is odd.  
    - Take two arguments and return their sum.  
    - Take two arguments and return `True` if their sum is odd.  
    - Take three arguments and return `True` if the product of the first two is less than or equal to the third.  

#### **Recursion**
8. Demonstrate recursion in Python to find the sum of `n` numbers.  
9. Develop a recursive Python function to compute the sum of elements in a nested list.  
    Example Input: `[1, 2, [3, 4], [5, 6]]`  
    Expected Output: `21`  
10. Write a Python script using recursion to find the nth Fibonacci number.  
11. Write a function to display the Fibonacci sequence up to the nth term where `n` is provided by the user.  
12. Design a recursive function to generate all subsets of a given list.  
13. Trace function calls and find the value of `h(6, 8)` for the function below:
```python
def h(m, n):  
	ans = 1  
	while n > 0:  
		ans, n = ans * m, n - 2  
	return ans  
```
   

#### **Factorial and Mathematical Constants**
13. What is recursion? Write a recursive function to calculate the factorial of a number.  
14. Using your factorial function, write a function to estimate the value of the mathematical constant `e`.  
15. Develop a factorial function which returns the factorial of a number. Using the factorial function, develop another function that estimates the value of the mathematical constant `e` using this formula:  
    `e = 1 + 1/1! + 1/2! + 1/3! + 1/4! + 1/5! + . .`

#### **Variable Arguments**
16. Explain variable-length argument functions with syntax and examples.  
17. Illustrate `*args` and `**kwargs` parameters in Python programming with examples.  

---

### **List Comprehension and Mapping**

1. What is list comprehension and `map` ? Describe with examples.  
2. Use list comprehension to create a list of integers specifying the length of each word in a sentence, excluding the word "the".  
    Example text:  
    `"The students of MCA study the programming language Python as part of the curriculum."`  

---

### **Lambda in Filtering and Mapping**

1. Using `filter`, write a lambda function that takes a list of numbers as input and generates a new list of prime numbers.  
2. Let `a` be the list of values produced by `range(1, 50)`. Using the function `filter` and a lambda argument, write expressions to produce the following:  
    - A list of odd numbers in `a`.  
    - A list of even numbers in `a`.  
    - A list of values in `a` divisible by 3 and not divisible by 7.  


### **Functional Programming and Lambda Functions**

1. Write short notes on anonymous functions in Python.
2. Implement the following using anonymous (lambda) functions:
    - Filter out only even numbers from a list.
    - Reduce a list of numbers to their sum.
3. Write a Python program using the `map` function to convert temperatures from Celsius to Fahrenheit and vice versa.
4. Using `reduce`, write a function named `ave(lst)` that will return the average of a list of numbers.
5. Analyze the output of the following code snippets:
    
```python
i) >>> filter(lambda x: x, [4, 0, 6, 3, 0, 2])
ii) >>> reduce(lambda x, y: x and y, filter(lambda x: x % 2 == 0, a))
```

---

### **Error Analysis and Debugging**

1. Analyze the following Python program, identify errors, and classify them as interpreter errors, runtime exceptions, or logic errors:  
```python
# Get two numbers from the user
n1, n2 = eval(input())  # 1

# Compute the sum of the two numbers
print(n1 + n2)  # 2

# Compute the average of the two numbers
print(n1 + n2 / 2)  # 3

# Compute a quotient
print(n1 / d1)  # 4

# Compute a product
n1 * n2 = d1  # 5
```  

---

### **Miscellaneous**

#### **Operations and Examples**
1. Discuss the difference between `map`, `filter`, and `reduce` with examples.  
2. Demonstrate the different types of function parameters available in Python.  
3. Create a generator in Python to yield all prime numbers in a range.  
4. Demonstrate the use of the `itertools` module in Python with examples.  
5. Explain keyword, required, and default function parameters with examples.  

#### **Special Implementations**
6. Design a simple calculator with different mathematical operations using a Python script.  
7. Write a Python script that takes a list of words and returns the length of the longest word using tuples.  
8. Design a Python program to find the middle number among three input numbers.  
9. Develop a Python program that will accept, as input, a series of names and salaries. Use the name ‘End’ to mark the end of the sequence of values. After the values have been entered, print the average salary and the names and salaries of those individuals with the highest and lowest salaries.

