
```python
>>> def sum(x,y):
...     s = x+y
...     return s
... 
>>> sum(2,3)
5
>>> if sum(2,3)>6:
...     print(True)
... else:
...     print(False)
... 
False



>>> def sum(x,y):
...     s = x+y
...     return s
... 
>>> sum(2,3)
5

```


**Program 1**
Create a function called `outer_function` that takes two parameters a and b. within this function, define an inner function called `inner_function` that returns the sum of a and b.

In outer_function, add 5 to the result from `inner_function` and return this final value to the caller.

```python
>>> def outer(a,b):
...     return inner(a+b)
... 
>>> def inner(a):
...     return a+5
... 
>>> outer(3,4)
12
```

```python
>>> def outer_func(a,b):
...     def inner_function():
...             return a+b
...     result = inner_function()
...     return result+5
... 
>>> print(outer_func(3,4))
12
```


***Program 2***
A palindrome is a string that reads the same forward and backwards.

Write a function names is_palindrome that accepts a string and checks whether it is a palindrome.

Te function should return true if it is a palindrome.

***Program 3***
A function to sum all the numbers in a list

***Program 4***
Function to print the even numbers from a list

***Program 5***
A function that accepts roll number and returns whether the student is present or absent