```python
>>> # Create two functions, sum of numbers() and product of numbers(), each using Python's *args to accept a variable number of numeric arguments.
>>> def sum_of(*num):
...     sum = 0
...     for i in num:
...             sum += i
...     return sum
... 
>>> def prod_of(*num):
...     prod = 1
...     for i in num:
...             prod *= i
...     return prod
... 
>>> sum_of([1,2,3,4])
TypeError: unsupported operand type(s) for +=: 'int' and 'list'
>>> sum_of(1,2,3,4)
10
>>> prod_of(1,2,3,4)
24

>>> # Create a function with variable length arguments
>>> prod_of(1,2,3,4,5,6,7)
5040
>>> sum_of(1,2,3,4,5,6,7)
28

```

```python
>>> # Local and Global variables
>>> 
>>> def func():
...     global x
...     x = 50
... 
>>> x = 10
>>> 
>>> func()
>>> print(x)
50
>>> 
>>> # LEGB Rule is a lookup procedure, which determines the order in which python looks for names
>>> # Local, Enclosing, Global, Built-in namespaces
>>> # name resolution
>>> 
>>> var = 100
>>> 
>>> def func():
...     return var
... 
>>> func()
100
>>> 
>>> var = 100
>>> def func():
...     print(var)
...     var = 200
...     return
... 
>>> func()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in func
UnboundLocalError: cannot access local variable 'var' where it is not associated with a value
>>> def func():
...     print(var)
...     
... func()
  File "<stdin>", line 4
    func()
    ^^^^
SyntaxError: invalid syntax

```

```python
>>> a = 10
>>> y = 5
>>> def func():
...     global a
...     y = a
...     a = 2
...     print(f"y = {y}, a = {a}")
...     print(a+y)
...     return a+y
... 
>>> print(f"y = {y}, a = {a}")
y = 5, a = 10
>>> func()
y = 10, a = 2
12
12
>>> print(f"y = {y}, a = {a}")
y = 5, a = 2
```

```python
>>> # For finding the sum of first n natural numbers,
>>> def factorial(n):
...     if(n==1):
...             return 1
...     return n+factorial(n-1)
... 
>>> factorial(3)
6
>>> factorial(5)
15
>>> factorial(10)
55
```

```python
>>> # Recursive factorial function and nCr calculation in python
>>> # nCr = n! / (r! (n-r)!)

>>> def ncr(n, r):
...     n = float(factorial(n))
...     r = float(factorial(r))
...     nr = float(factorial(n-r))
...     return float(n/r*nr)
... 
>>> ncr(3,2)
12.0
>>> ncr(5,2)
390.0
>>> ncr(7,2)
3033.3333333333335
```

```python
>>> # Recursive Factorial function and Estimating Euler's Constant (e)

```

```python
>>> # Function to count Digit, Upper and Lowercase Letters


```



