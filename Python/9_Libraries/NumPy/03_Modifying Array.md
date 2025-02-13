
___

`flatten()`function returns a copy of the array collapsed into one dimension.

```python
>>> arr = np.array([[1,2,3], [4,5,6], [7,8,9] ])
>>> print(arr.flatten())
[1 2 3 4 5 6 7 8 9]
```

___


`reshape()`

To change the shape of an array without modifying its data.
Total elements remain the same, but rows columns change.

if a 1D array has 6 elements, is can be reshaped into  2D array of form `2x3, 3x2, 1x6,`

```python
>>> import numpy as np
>>> arr = np.arange(10)
>>> print(arr)
[0 1 2 3 4 5 6 7 8 9]

>>> re = arr.reshape(5,2)
>>> print(re)
[[0 1]
 [2 3]
 [4 5]
 [6 7]
 [8 9]]

>>> re = arr.reshape(2,5)
>>> print(re)
[[0 1 2 3 4]
 [5 6 7 8 9]]
```

`reshape(arrayname, (n, r, c))`
n indicates the number of arrays in the resultant array.

```python
>>> arr = np.array([[ [1,2,3,4],[5,6,7,8]],[[11,12,13,14],[15,1,3,5]]])

>>> re = arr.reshape(4,4)
>>> print(re)
[[ 1  2  3  4]
 [ 5  6  7  8]
 [11 12 13 14]
 [15  1  3  5]]

>>> # Using proper syntax without n makes 2D array
>>> re = np.reshape(arr, (4,4))
>>> print(re)
[[ 1  2  3  4]
 [ 5  6  7  8]
 [11 12 13 14]
 [15  1  3  5]]
```

```python
>>> # specifying n, makes it a 3D array with n arrays
>>> arr = np.arange(16)
>>> re = np.reshape(arr, (2,4,2))
>>> print(re)
[[[ 0  1]
  [ 2  3]
  [ 4  5]
  [ 6  7]]

 [[ 8  9]
  [10 11]
  [12 13]
  [14 15]]]

>>> re = np.reshape(arr, (1,4,4))
>>> print(re)
[[[ 0  1  2  3]
  [ 4  5  6  7]
  [ 8  9 10 11]
  [12 13 14 15]]]
```

```python
>>> arr = np.arange(12)
>>> print(arr)
[ 0  1  2  3  4  5  6  7  8  9 10 11]

>>> re = np.reshape(arr, (3,2,2))
>>> print(re)
[[[ 0  1]
  [ 2  3]]

 [[ 4  5]
  [ 6  7]]

 [[ 8  9]
  [10 11]]]

```



___

`resize()` used to change the shape and size of an array
The missing elemts will be filled with zeroes
It happens in place, does not return anything

```python
>>> arr = np.array([[1,2,3],[4,5,6] ])
>>> print(arr.resize(3,3))
None

>>> arr.resize(3,3)
>>> print(arr)
[[1 2 3]
 [4 5 6]
 [0 0 0]]

>>> arr = np.array([[1,2,3],[4,5,6],[8,9,10] ])
>>> arr.resize(2,2)
>>> print(arr)
[[1 2]
 [3 4]]
>>> arr.resize(4,4)
>>> print(arr)
[[1 2 3 4]
 [0 0 0 0]
 [0 0 0 0]
 [0 0 0 0]]

>>> arr = np.array([[1,2,3],[4,5,6],[8,9,10] ])
>>> arr.resize(4,4)
>>> print(arr)
[[ 1  2  3  4]
 [ 5  6  8  9]
 [10  0  0  0]
 [ 0  0  0  0]]

```


___

`arr.T`   Transposes the given arrays rows and columns

```python
>>> import numpy as np
>>> arr = np.array([ [2,3,4,5],[5,2,4,5] ])
>>> print(arr.itemsize )
8
>>> print(arr.nbytes)
64
>>> print(arr.T)
[[2 5]
 [3 2]
 [4 4]
 [5 5]]
```
