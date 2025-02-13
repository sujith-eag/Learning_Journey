
### Comparing Arrays
`<  >   >=   <=   ==   !=` to compare arrays of the same size.
They compare the corresponding elements of the arrays and returns another array with boolean type value.
So resultant arrays will contain true or false.


```python
>>> arr1 = np.array([10, 20, 30.5, -40])
>>> arr2 = np.array([ 1, 2, 3, 4 ])
>>> c = a==b
>>> c = arr1 == arr2
>>> d = arr1 != arr2
>>> e = arr1 < arr2
>>> f = arr1 > arr2
>>> print(c)
[False False False False]
>>> print(d)
[ True  True  True  True]
>>> print(e)
[False False False  True]
>>> print(f)
[ True  True  True False]
```

___

`any()` and `all()`
`any()` is used to check if one of the value in the array is true,
`all()` is used to check if all are true
The result of these will be True or False.
```python
>>> print(d)
[ True  True  True  True]
>>> print(any(d))
True
>>> print(all(d))
True

>>> print(c)
[False False False False]
>>> print(any(c))
False
```

____

`logical_and()`  and `logical_or()` and `logical_not()` are useful to get the boolean array as a result of comparing the compound condition.
`c = logical_and(a>0, a<4)` 
The two conditions are applied on every element in the array and and returns another array that has True or False values.

```python
>>> import numpy as np
>>> a = np.array([1,2,3])
>>> b = np.array([3,2,1])

>>> c = np.logical_and(a>0, a<4)
>>> print(c)
[ True  True  True]

>>> d = np.logical_and(a<b, a==2)
>>> print(d)
[False False False]

>>> e = np.logical_or(a<b, b==2)
>>> print(e)
[ True  True False]


>>> d = np.logical_and(a<b, a=2)
TypeError: logical_and() takes from 2 to 3 positional arguments but 1 were given
```


___

`where()` function can be used to create a new array based on whether a given condition is true or false.
`arr = np.where(condition, expression1, expression2)`

If the condition is true, then the expression 1 is executed and the result is stored into the array.
else expression 2 is executed and stored.

```python
>>> a = np.array([10, 21, 30, 41, 50], int)
>>> c = np.where(a%2, a, 0)
>>> print(c)
[ 0 21  0 41  0]


>>> arr = np.array([1,2,3,4,5,6,7,8])
>>> c = np.where(arr%2==0, arr, 0 )
>>> print(c)
[0 2 0 4 0 6 0 8]

>>> arr2 = np.array([[1,2,3,4],[5,6,7,8] ])
>>> c = np.where( arr2%2==0, arr2, 0 )
>>> print(c)
[[0 2 0 4]
 [0 6 0 8]]
```
Here, the condition `arr%2==0` is applied on each element in the array and is stored in the array. then element is stored in the array else 0 is stored.

Comparing elements of array and taking the largest one.
```python
>>> arr2 = np.array([[1,2,3,4],[5,6,7,8] ])
>>> arr1 = np.array([[2,3,4,5],[10,11,12,3] ])
>>> lar = np.where(arr1>arr2, arr1, arr2)
>>> print(lar)
[[ 2  3  4  5]
 [10 11 12  8]]

```

___

`nonzero()` is a function that returns the index of the values which are not zero. The zero elements indexes are not included.
```python

>>> arr = np.array([1,2,3,4,5,6,7,8])
>>> d = np.nonzero(arr)
>>> print(d)
(array([0, 1, 2, 3, 4, 5, 6, 7]),)

>>> arr = np.array([2,4,5,0,6,0,20,0])
>>> d = np.nonzero(arr)
>>> print(d)
(array([0, 1, 2, 4, 6]),)
```

```python
>>> arr1 = np.array([[2,0,4,5],[10,11,0,3] ])
>>> c = np.nonzero(arr1)
>>> print(c)
(array([0, 0, 0, 1, 1, 1]), array([0, 2, 3, 0, 1, 3]))


[ [ 2,  0,  4,  5],
  [10, 11,  0,  3]   ]

```
`np.nonzero(arr1)` returns a tuple of two arrays:

The first array contains the row indices(which array) of non-zero elements.
The second array contains the corresponding column( position in array) indices of those non-zero elements.
- The first non-zero element is at `(0, 0)` (value `2`).
- The second non-zero element is at `(0, 2)` (value `4`).
- The third non-zero element is at `(0, 3)` (value `5`).
- The fourth non-zero element is at `(1, 0)` (value `10`).
- The fifth non-zero element is at `(1, 1)` (value `11`).
- The sixth non-zero element is at `(1, 3)` (value `3`).


To retrieve non zero elements from the array
```python
>>> arr = np.array([2,4,5,0,6,0,20,0])
>>> c = np.nonzero(arr)
>>> print(c)
(array([0, 1, 2, 4, 6]),)
>>> print(arr[c])
[ 2  4  5  6 20]

>>> for i in c:
...     print(i)
...
[0 1 2 4 6]
```



