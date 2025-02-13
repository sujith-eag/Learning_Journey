
Dimensions of an array represents the arrangements of elements in the array.

Horizontal arrangements is row and vertical is column

An array with only one row or only one column is called 1 dimensional array (1D array)

```python
arr = np.array( [1,2,3,4] )

arr1 = np.array( [ 10, 
					20,
					30,
					40])
```

```python
>>> import numpy as np
>>> arr = np.array([1,2,3,4])
>>> print(arr)
[1 2 3 4]
```

### Multidimensional arrays (Matrix)

Two dimensional array contains more than one row or one column. which means has multiple 1D arrays.
```python
arr = np.array( [[1,2,3]
				[4,5,6]] )
```

```python
>>> # 2 rows, 4 colums
>>> arr = np.array([[1,2,3,4],[5,6,7,8]])
>>> print(arr)
[[1 2 3 4]
 [5 6 7 8]]

>>> # 3 rows 4 columns
>>> arr = np.array([[1,2,3,4],[5,6,7,8],[11,12,13,14]])
>>> print(arr)
[[ 1  2  3  4]
 [ 5  6  7  8]
 [11 12 13 14]]
```

A 3D array contains multiple 2D arrays.
```python
>>> # has two 2D arrays, each 2D array contains 2 rows, 4 columns
>>> arr = np.array([[ [1,2,3,4],[5,6,7,8]],[[11,12,13,14],[15,1,3,5]]])
>>> print(arr)
[[[ 1  2  3  4]
  [ 5  6  7  8]]

 [[11 12 13 14]
  [15  1  3  5]]]
```

The number of rows and columns have to match
```python
>>> arr = np.array([ [1,2,3,4],[5,6,7,8],[11,12] ])
ValueError: setting an array element with a sequence. The requested array has an inhomogeneous shape after 1 dimensions. The detected shape was (3,) + inhomogeneous part.

>>> arr = np.array([ [[1,2,3,4],[5,6,7,8]],
>>> 					[[11,12,13,14]]     ])
ValueError: setting an array element with a sequence. The requested array has an inhomogeneous shape after 1 dimensions. The detected shape was (2,) + inhomogeneous part.
```

___

