
Generators are functions that return a sequence of values.

It is written like an ordinary function but it uses `yield` statement which returns the values.

A generator function that generates numbers from x to y.

```python
def range_gen(x, y):
	while x<=y:
		yield x
		x += 1

g = range_gen(5, 10)

for i in g:
	print( i, end=' ')
# 5 6 7 8 9 10

lst = list( g )
print(lst)
# []    empty list
```


When the generator function is called with parameters, the `range_gen` function returns a generator object with the sequence of numbers from 5 to 10 ( yielding values each iteration of loop). 
`g`  is the generator object, it can be stored into a list.
We can display the numbers from `g` using a for loop.

This loop consumes the generator `g` by yielding values one at a time. So, when the loop finishes, `g` is exhausted.

```python
>>> def range_gen(x,y):
...     while x<=y:
...             yield x
...             x += 1
... 

>>> g = range_gen(5, 10)
>>> lst = list(g)
>>> g
<generator object range_gen at 0x77ccf28c9900>

>>> lst
[5, 6, 7, 8, 9, 10]

>>> lst2 = list(g)
>>> lst2
[]
```

___

- **Generators are stateful**: They remember where they left off. Once they yield all their values, they are considered "exhausted," meaning they can't produce more values unless you recreate the generator object.
- **Generators are not reusable**: After a generator finishes, it cannot be restarted or "rewound." You would need to create a new generator instance if you want to iterate over the range again.

``
___

we can use the `next()` function to retrieve the elements one by one from the generator object each time next() is called.

`print( next(g) )` will display the first element when it is called once, repeatedly calling is needed to access each element.

```python
>>> def mygen():
...     yield 'A'
...     yield 'B'
...     yield 'C'
... 
>>> g = mygen()
>>> 
>>> print(next(g))
A
>>> print(next(g))
B
>>> print(next(g))
C
>>> print(next(g))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration

```