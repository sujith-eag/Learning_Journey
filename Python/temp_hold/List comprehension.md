List comprehension
represents creation of a new list from an iterable object ( like a list, set, tuple, dictionary or range) that satisfy a given condition.

It is very compact code, usually a single line.

```python
>>> square = []
>>> for i in range(1,11):
...     square.append(i**2)
... 
>>> square
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

```python
>>> squares = [x**2 for x in range(3,11)]
>>> squares
[9, 16, 25, 36, 49, 64, 81, 100]
```

So a list comprehension consists of `[]` square braces, containing an expression up front. after the expression, a for loop and then zero or more if statements can be written.

```python
[expression  for item1 in iterable1  if statement1
			for item2 in iterable2 if statement2
			for item3 in iterable3 if statement3 ....]
```
Here iterable represents a list, set, dict, range, tuple.
The result is a new list which contains elements formed as a result of executing the expression according to the for loop and if statements.

To get only square of even numbers

```python
>>> [x**2 for x in range(3,11)]
[9, 16, 25, 36, 49, 64, 81, 100]

>>> [x**2 for x in range(1,11) if x%2==0]
[4, 16, 36, 64, 100]

>>> [x**2 for x in range(2,11,2)]
[4, 16, 36, 64, 100]
```

Adding two add each element of a list to each element of another list.
```python
>>> x = [10, 20, 30]
>>> y = [1,2,3,4]
>>> [i+j for i in x for j in y]
[11, 12, 13, 14, 21, 22, 23, 24, 31, 32, 33, 34]

>>> [i+j for i in [10, 20, 30] for j in [1,2,3,4]]
[11, 12, 13, 14, 21, 22, 23, 24, 31, 32, 33, 34]
```

Using traditional loops
```python
>>> lst = []
>>> for i in x:
...     for j in y:
...             lst.append(i+j)
... 
>>> lst
[11, 12, 13, 14, 21, 22, 23, 24, 31, 32, 33, 34]
```

Selecting numbers not in a list
```python
>>> [i for i in [1,2,3,4,5] if i not in [10,11,1,2]]
[3, 4, 5]

>>> A = [1,2,3,4,5]
>>> B = [10,11,1,2]
>>> [i for i in A if i not in B]
[3, 4, 5]
```

For string
```python
>>> [i+j for i in 'ABC' for j in 'DE']
['AD', 'AE', 'BD', 'BE', 'CD', 'CE']
```
Extracting the first letter into a list.
```python
>>> words = ['Apple', 'Banana', 'Grapes', 'Orange' ]
>>> [word[0] for word in words]
['A', 'B', 'G', 'O']
```


___

Similarly it is also possible to create dictionary comprehension and set comprehension. for dictionary the braces will be `{}`

To convert value to key and key to value in a dictionary
```python
>>> rev_dict = { value:key for key,value in dict.items() }
```

