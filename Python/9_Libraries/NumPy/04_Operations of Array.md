
Mathematical operations of Arrays

The functions of math module can be applied on the elements of an array.

```python
>>> arr = np.array([[1,2,3],[4,5,6],[8,9,10] ])
>>> arr = arr+5
>>> print(arr)
[[ 6  7  8]
 [ 9 10 11]
 [13 14 15]]
>>> arr = arr-4

>>> print(arr)
[[ 2  3  4]
 [ 5  6  7]
 [ 9 10 11]]
>>> arr = arr*2

>>> print(arr)
[[ 4  6  8]
 [10 12 14]
 [18 20 22]]
>>> arr = arr/2

>>> print(arr)
[[ 2.  3.  4.]
 [ 5.  6.  7.]
 [ 9. 10. 11.]]

```

Operations on two different arrays (with same shape)

```python
>>> arr1 = np.array([10, 20, 30.5, -40])
>>> arr2 = np.array([ 1, 2, 3, 4  ])
>>> arr3 = arr1 - arr2
>>> print(arr3)
[  9.   18.   27.5 -44. ]

>>> arr3 = arr1 + arr2
>>> print(arr3)
[ 11.   22.   33.5 -36. ]

>>> arr3 = arr1 * arr2
>>> print(arr3)
[  10.    40.    91.5 -160. ]

```


```python
>>> arr = np.array([[1,2,3],[4,5,6],[8,9,10] ])
>>> arr2 = np.array([[1,2,3],[4,5,6],[8,9,10] ])
>>> arr3 = arr * arr2
>>> print(arr3)
[[  1   4   9]
 [ 16  25  36]
 [ 64  81 100]]
```
These kinds of operations are called as vectorised operations since entire array is (or vector ) is processed just like a variable.

These are important because they are faster, Cleaner syntactically so provide cleaner code.

The mathematical functions in numpy
```
max(arr)   min(arr)    sum(arr)

mean(arr)  median(arr)  

argmax(arr)  argmin(arr)   # index of max and min

sort(arr)

unique(arr)   concatenate([a,b])

sin(arr)   cos(arr)    tan(arr)

```






___

Aggregation functions
for one dimension arrays only
`np.sum(arr)  np.mean(arr)  np.max(arr)  `

for Two dimensional array can be specified to sum along the rows and columns
`np.sum(arr, axis=0)`   Sum along the columns
`np.sum(arr. axis=1)` sum along the rows
`np.sum(arr)` will sum everything into one number


```python
>>> arr = np.array([[1,2,3],[4,5,6],[8,9,10] ])
>>> totalSum = np.sum(arr)
>>> print(totalSum)
48
>>> alongcolumn = np.sum(arr, axis=0)
>>> print(alongcolumn)
[13 16 19]
>>> alongRows = np.sum(arr, axis=1)
>>> print(alongRows)
[ 6 15 27]
```

```python
>>> arr = np.array([[1,2,3],[4,5,6],[8,9,10] ])
>>> meanCol = np.mean(arr, axis=0)
>>> print(meanCol)
[4.33333333 5.33333333 6.33333333]

>>> meanRows = np.mean(arr, axis=1)
>>> print(meanRows)
[2. 5. 9.]
```

```python
>>> a = np.array([1,4,6,8,9])
>>> print(np.min(a))
1
>>> print(np.max(a))
9
```

```python
>>> arr = np.array([[1,2,3],[4,5,6],[8,9,10] ])
>>> print(np.max(arr))
10
>>> print(np.max(arr, axis=0))
[ 8  9 10]
>>> print(np.max(arr, axis=1))
[ 3  6 10]
>>> print(np.min(arr, axis=1))
[1 4 8]
>>> print(np.min(arr, axis=0))
[1 2 3]

```
____


`np.maximum(arr, arr1)` is used to compare two arrays and return a new array containing the maximum values at each corresponding position.
`np.minimum(arr, arr1)` to return the minimum of two arrays.

```python
>>> a = np.array([1,4,6,8,9])
>>> b = np.array([5,7,3,9,22])
>>> print(np.maximum(a,b))
[ 5  7  6  9 22]
>>> print(np.minimum(a,b))
[1 4 3 8 9]
```

