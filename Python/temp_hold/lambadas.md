
A function without a name is called 'anonymous function'.

they are not defined using `def` keyword but by `lambda`

```python
def square(x):
	return x * x

lambda x: x*x
```
What is given after lambda is the argument for the function, colon `:` is the beginning of the function that has the expression.

`lambda argument_list : expression`

They contain only one expession.
There is no need to write return statement, Lambda function always returns a value by default, so it should be assigned to a variable, which becomes the function call.
`f = lambda x: x*x`
Here `f` is the function call so `value = f(5)` returns 25

`f = lambda x, y: x+y` 
`result = f(1.5, 10)`
`print('sum = ', result)`
`print(f(2,5))  ` 

___

Using Lambda with `filter()` function
filter() function is useful to filter out the elements of the sequence depending on the result of a function.

We should apply a function and a filter to a function.
`filter(function, sequence)`
Here function represents a function which returns either true or false:
sequence represents a list, string or tuple.

The function is applied to every element and when  the function returns true it is the element is extracted.

```python
>>> lst = [10, 11, 12, 13, 14, 15, 16, 17]
>>> lst_even = list( filter( lambda x: (x % 2 == 0),  lst ) )
>>> lst_even
[10, 12, 14, 16]
# or just 
>>> list( filter( lambda x: (x % 2 == 0),  lst ) )
[10, 12, 14, 16]
```
Using a traditional def way for function
```python
>>> lst = [10, 11, 12, 13, 14, 15, 16, 17]
>>> def is_even(x):
...     if x%2 == 0:
...             return True
...     else:
...             return False
... 
>>> lst_ev = list( filter( is_even, lst  ) )
>>> lst_ev
[10, 12, 14, 16]

```


___

It is possible to use map() function on more than one list if the lists are of the same length.
So map() functions takes the lists as arguments of the lambda function and does the operation.

`map( lambda x, y: x*y, lst1, lst2) `
The values from each list and multiplied and product is returned, by taking each as x and y from each list.

```python
>>> lst1 = [10, 11, 12, 13, 14, 15, 16, 17]
>>> lst2 = [2, 1, 0, 33, 1, 45, 236, 23]
>>> list( map( lambda x,y: x*y, lst1, lst2 ) )
[20, 11, 0, 429, 14, 675, 3776, 391]
```

___ 
Using Lambda with reduce function

The reduce function reduces a function to a single value by processing the elements according to a function supplied.
`reduce(function, sequence)`

reduce has been moved to `functools` so has to be imported
```python
>>> from functools import reduce
>>> lst = [10, 11, 12, 13, 14, 15, 16, 17]
>>> reduce(lambda x, y: x*y, lst)
980179200

>>> reduce( lambda x, y: x+y, range(1,51))
1275
```

reduce is taking two elements and returning their product, the product is multiplied with the third and so on and the final product is returned.


