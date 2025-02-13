

Single dimension and Multi dimensional array

```python
>>> import numpy as np
>>> arr = np.array([1,2,2,3])
>>> print(arr)
[1 2 2 3]
```

```python
>>> from numpy import *
>>> arr = array([1,2,3,4])
>>> print(arr)
[1 2 3 4]
```

___

Creating Arrays using array()

```python
arr = np.array([1,2,3,4], int)

arr = np.array([1.5, 2.4, 3.2], float)
```
Type of array can be declared but it is not necessary as numpy will see one and convert everything to float with decimal.

For an array of character type or string type, need not define anything ( but `dtype = str` can work)
```python
arr = np.array(['a', 'b', 'c'])
```


```python
>>> arr = np.array([[1,2,3,4],[5,6,7,8]])
>>> print(arr)
[[1 2 3 4]
 [5 6 7 8]]
```
Even though the elements are displayed in 2 rows and 4 columns, the internal memory allocated to all these elements would be in the form of a single row containing 8 blocks.
with indexes `[0][0]` `[0][1]` upto `[1][3]`

___

Aliasing the array,
```python
>>> import numpy as np
>>> a = np.array([1,2,3,4])   # original array
>>> b = np.array(a)     # creating b from array function
>>> c = a    # creating c by assigninment
>>> print("a = ", a)
>>> print("b = ", b)
>>> print("c = ", c)

a =  [1 2 3 4]
b =  [1 2 3 4]
c =  [1 2 3 4]
```

`c = a` will not make a new copy of an array a, so b is not a new array with different memory.
So now a and b are referring to the same array which is known as aliasing.

`view()` is used to create a new array that is same as an existing array. They will be have the same elements but will have different memory locations.
Since they are mirror images, if original array is modified, then the new array is also modified.
```python
>>> a = np.array([4,5,6,7])
>>> arr = np.array([4,5,6,7])
>>> arr2 = arr.view()
>>> print(arr2)
[4 5 6 7]
>>> arr[1] = 10
>>> print(arr2)
[ 4 10  6  7]
```

To have two arrays which are independent, then 'deep copying' is done using `copy()` to create a new array that is copy of original array.

```python
>>> arr = np.array([ [2,3,4,5], [5,2,4,5] ])
>>> b = np.copy(arr)
>>> print(b)
[[2 3 4 5]
 [5 2 4 5]]
 
>>> arr[0][1] = 33
>>> print(b)
[[2 3 4 5]
 [5 2 4 5]]
>>> print(arr)
[[ 2 33  4  5]
 [ 5  2  4  5]]
```



___

`linespace()` is used to create an array with evenly spaced points between a starting and ending point.

`np.linspace([start, stop, n])`

```python
>>> import numpy as np
>>> a = np.linspace(0, 10, 5)
>>> print(a)
[ 0.   2.5  5.   7.5 10. ]
```

starting from 0 and ending at 10, it is divided into 5 equal parts.

If the number of steps is omitted, it will be taken as 50 which is default.

```python
>>> b = np.linspace(0,10)
>>> print(b)
[ 0.          0.20408163  0.40816327  0.6122449   0.81632653  1.02040816
  1.2244898   1.42857143  1.63265306  1.83673469  2.04081633  2.24489796
  2.44897959  2.65306122  2.85714286  3.06122449  3.26530612  3.46938776
  3.67346939  3.87755102  4.08163265  4.28571429  4.48979592  4.69387755
  4.89795918  5.10204082  5.30612245  5.51020408  5.71428571  5.91836735
  6.12244898  6.32653061  6.53061224  6.73469388  6.93877551  7.14285714
  7.34693878  7.55102041  7.75510204  7.95918367  8.16326531  8.36734694
  8.57142857  8.7755102   8.97959184  9.18367347  9.3877551   9.59183673
  9.79591837 10. 
```

____

creating arrays using logspace

`logspace()`

___

Creating an array using `arrange()` function
It is similar to `range()` in pyhton
```python
arange(start, stop, stepsize)
```

```python
>>> print(np.arange(10))
[0 1 2 3 4 5 6 7 8 9]
>>> print(np.arange(0,10))
[0 1 2 3 4 5 6 7 8 9]
>>> print(np.arange(0,10,2))
[0 2 4 6 8]
>>> print(np.arange(0,10,3))
[0 3 6 9]
>>> print(np.arange(0,10,4))
[0 4 8]
>>> print(np.arange(0,10,1.5))
[0.  1.5 3.  4.5 6.  7.5 9. ]
>>> print(np.arange(10,1,-1))
[10  9  8  7  6  5  4  3  2]
>>> print(np.arange(2,11,2))
[ 2  4  6  8 10]

```

___
Creating arrays using `zeros()` and `ones()` function
`zeros(n, datatype)`
`ones(n, datatype)`

If the datatype is omitted, the default is float.

```python
>>> arr = np.zeros(6, int)
>>> print(arr)
[0 0 0 0 0 0]

>>> arr = np.zeros(6, float)
>>> print(arr)
[0. 0. 0. 0. 0. 0.]

>>> arr = np.ones(6, float)
>>> print(arr)
[1. 1. 1. 1. 1. 1.]

>>> arr = np.ones(6, int)
>>> print(arr)
[1 1 1 1 1 1]
```

these can be used to create 2D arrays with rows and columns.
`ones((r,c), dtype)`
`zeros((r,c), dtype)`

```python
>>> arr = np.ones((3,6))
>>> print(arr)
[[1. 1. 1. 1. 1. 1.]
 [1. 1. 1. 1. 1. 1.]
 [1. 1. 1. 1. 1. 1.]]

>>> arr = np.ones((3,6),int)
>>> print(arr)
[[1 1 1 1 1 1]
 [1 1 1 1 1 1]
 [1 1 1 1 1 1]]

>>> arr = np.zeros((3,6))
>>> print(arr)
[[0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0.]
 [0. 0. 0. 0. 0. 0.]]

>>> arr = np.zeros((3,6), int)
>>> print(arr)
[[0 0 0 0 0 0]
 [0 0 0 0 0 0]
 [0 0 0 0 0 0]]
```


___

`eye()` function creates a 2D array and fills the elements in the diagonal with 1s. It can only create a square matrix of `nxn` form, so takes only one parameter.

`eye(n, dtype=datatype)`

```python
>>> arr = np.eye(4)
>>> print(arr)
[[1. 0. 0. 0.]
 [0. 1. 0. 0.]
 [0. 0. 1. 0.]
 [0. 0. 0. 1.]]

>>> arr = np.eye(4, dtype=int)
>>> print(arr)
[[1 0 0 0]
 [0 1 0 0]
 [0 0 1 0]
 [0 0 0 1]]
```

