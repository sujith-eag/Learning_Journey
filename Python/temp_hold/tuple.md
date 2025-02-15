
immutable so no `append, extend, insert, remove, pop, clear`

It is meant for storing data which should not be modified and retrieve data on demand.

```python
>>> tup = ()
>>> tup
()

>>> tup = 1,2,3,4
>>> tup
(1, 2, 3, 4)
```

```python
>>> tup = (10,)
>>> tup
(10,)
>>> type(tup)
<class 'tuple'>

>>> tup = (10)
>>> tup
10
>>> type(tup)
<class 'int'>
```

```python
>>> tpl = (1, 2, 3, "apple", 4.5)
>>> tpl
(1, 2, 3, 'apple', 4.5)
```

Converting a list and range into a tuple
```python
>>> lst = [1,2,3,4]
>>> tuple(lst)
(1, 2, 3, 4)

>>> tuple(range(4,9,2))
(4, 6, 8)
```