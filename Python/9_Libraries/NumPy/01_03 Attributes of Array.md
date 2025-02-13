Numpy's array class is called `ndarray`. It is known by alias name `array`.
There is another class `array` in python which is different from numpy `array` class.

___

`ndim` attribute
represents the number of dimensions or axes(rank) of the array. 

```python
>>> arr = np.array([1,2,3,4])
>>> print(arr.ndim)
1
>>> arr = np.array([[1,2,3,4],[5,6,7,8],[11,12,13,14]])
>>> print(arr.ndim)
2
>>> arr = np.array([[ [1,2,3,4],[5,6,7,8]],[[11,12,13,14],[15,1,3,5]]])
>>> print(arr.ndim)
3
```


___

shape attribute
it gives the shape of an array(rows and columns)
The shape is a tuple listing the number of elements along each dimension(axis)

for 1D array, shape gives the number of elements.
for 2D array, it specifies number of rows and columns 

```python
>>> arr = np.array([1,2,3,4])
>>> print(arr.shape)
(4,)

>>> arr = np.array([[1,2,3,4],[5,6,7,8],[11,12,13,14]])
>>> print(arr.shape)
(3, 4)
```

```python
>>> arr = np.array([[ [1,2,3,4],[5,6,7,8]],[[11,12,13,14],[15,1,3,5]]])
>>> print(arr)
[[[ 1  2  3  4]
  [ 5  6  7  8]]

 [[11 12 13 14]
  [15  1  3  5]]]
  
>>> print(arr.shape)
(2, 2, 4)

>>> print(arr.size)
16
```

____

size attribute
gives the total number of elements in the array.


___

`itemsize` attribute    
returns the memory size of the array elements in bytes.
`arr.nbyte`    The total size of byte of all items

```python
>>> arr = np.array([[ [1,2,3,4],[5,6,7,8]],[[11,12,13,14],[15,1,3,5]]], int)
>>> print(arr.itemsize)
8
>>> arr = np.array([[ [1,2,3,4],[5,6,7,8]],[[11,12,13,14],[15,1,3,5]]], float)
>>> print(arr.itemsize)
8

```


___

