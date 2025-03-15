

Create a function called `outer_function` that takes two parameters, `a` and `b`. 
Within this function, define an inner function called `inner_function` that returns the sum of `a` and `b`.

In `outer_function`, add 5 to the result from `inner_function` and return this final value to the caller.

```python
>>> def outer(a,b):
...     def inner(a,b):
...             return a+b
...     return inner(a,b)+5
... 
>>> 
>>> outer(2,3)
10
>>> outer(5,5)
15
```

___

Define **two** Python functions to determine the largest of three numbers.
- Create a helper function that takes **two numbers** and returns the **larger** one.
- Create a main function that takes **three numbers**, uses the helper function to compare values, and returns the **largest** of the three.

```python
>>> def main():
...     a = int(input("Enter a: "))
...     b = int(input("Enter b: "))
...     c = int(input("Enter c: "))
...     def compare(a,b,c):
...             return max(a,b,c)
...     max_val = compare(a,b,c)
...     return max_val
... 

>>> main()
Enter a: 1
Enter b: 2
Enter c: 3
3

>>> main()
Enter a: 3
Enter b: 16
Enter c: 1
16
```

____

Create two functions, `sum_of_numbers()` and `product_of_numbers()`, each using Python’s `*args` to accept a variable number of numeric arguments.
- `sum_of_numbers()` should return the total of all numbers passed in.
- `multiply_numbers()` should return the product of all numbers passed in.
- For example, `sum_of_numbers(1, 2, 3, 4)` should return 10 and `multiply_numbers(1, 2, 3, 4)` should return 24."

```python
>>> def sum_of_numbers(*numbers):
...     sum = 0
...     for i in numbers:
...             sum += i
...     return sum
... 
>>> def multiply_numbers(*numbers):
...     prod = 1
...     for i in numbers:
...             prod *= i
...     return prod
... 
>>> sum_of_numbers(2,2,2,4)
10
>>> sum_of_numbers(7,5,3,2)
17
>>> multiply_numbers(3,4,5,6)
360
>>> multiply_numbers(3,4)
12
```

____

Define a Python recursive function to print the Fibonacci series up to n_terms.

```python

```


____

Write a Python program that allows the user to **choose** between computing a **factorial** or printing a **Fibonacci series (without recursion)**.

```python

```

___

Write a menu-driven Python program that lets the user **check if a number is even/odd** or **prime**.
```python

```

___

Write a Python program that allows the user to **reverse a number** or **reverse a string. reverse a number without converting it into a string also check if the given number is a palindrome.**

```python

```

___

Write a menu-driven Python program that displays the following patterns:

```
1. * * * * ii) *
    

* * * * *

* * * * *

* * * * *
```

___

WAP to read roll number and marks of n students and create a dictionary from it having roll numbers as keys.

```python

```

___

Write a python program that accepts a string and calculate the number of uppercase, lowercase, digits and special characters
```python

```

___

Write a Python program that demonstrates the use of five different list methods. Your program should:

1. Create a list and allow the user to add elements using the append() method.
    
2. Insert an element at a specific position using the insert() method.
    
3. Remove a specific element from the list using the remove() method.
    
4. Sort the list in ascending order using the sort() method.
    
5. Display the index of any element in the list using the index() method.

```python

```

___

Write a Python program that demonstrates the following:

1. Create and check the shape of an array
    
2. Convert a 1D array of 12 elements into a 3x4 matrix.
    
3. Convert a 2D or 3D array into a 1D array
    
4. Extract a subarray using slicing
    
5. Extract every alternate element from a given array

```python

```

___

Write regular expressions to validate the following inputs:

1. Email Address – Ensure it follows the standard email format (e.g., user@example.com).
    
2. Date – Match a date in the format DD/MM/YYYY or MM-DD-YYYY.

```python

```

___

Write regular expressions to validate the following inputs:

1. URL – Validate a URL that starts with http:// or https:// and includes a domain name.
    
2. Phone Number – Validate a phone number that may optionally contain two dashes (e.g., 123-456-7890 or 1234567890).

```python


```


____

