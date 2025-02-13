
Slicing is extracting a range of elements from an array.

`arrayname[start:stop:stepsize]`
default for start is 0, and stop is number of elements, `stepsize` is 1.

```python
>>> arr = np.array([4,5,6,7,9,1,2])

>>> print(arr[::])
[4 5 6 7 9 1 2]

>>> print(arr[1:4])
[5 6 7]
>>> print(arr[1:4:2])
[5 7]
>>> print(arr[1::2])
[5 7 1]
>>> print(arr[1::])
[5 6 7 9 1 2]
>>> print(arr[1::-1])
[5 4]          # went in reverse
>>> print(arr[:0:-1])   # stops before 0
[2 1 9 7 6 5]
>>> print(arr[::-1])  # end to start
[2 1 9 7 6 5 4]
>>> print(arr[-1:-4:-1])
[2 1 9]

```


___

Indexing refers to the location of the elements. It is from 0 to n-1 which can be used to refer to all elements as `arr[0]` `arr[1]` `arr[n-1]`


```python
>>> a = np.arange(10,16)
>>> i = 0
>>> while(i<len(a)):
...     print(a[i])
...     i += 1
... 
10
11
12
13
14
15
>>> for j in range(len(a)):
...     print(a[j])
... 
10
11
12
13
14
15

>>> a = np.arange(10,50)
>>> b = a[::5]
>>> for i in range(len(b)):
...     print(a[i], end=', ')
... 
10, 11, 12, 13, 14, 15, 16, 17,
```


___

#### Indexing in Multidimensional Array
The individual elements of a 2D array can be accessed by specifying the row and column.

```python
>>> arr = np.array([[1,2,3,4],[5,6,7,8]])

>>> print(arr[0])
[1 2 3 4]

>>> print(arr[0][0])
1
```
 To access each element in a 2D array.

```python
>>> arr = np.array([[1,2,3,4],[5,6,7,8]])
>>> print(len(arr))
2
>>> print(len(arr[0]))
4

>>> for i in range (len(arr)):
...     print(arr[i])
... 
[1 2 3 4]
[5 6 7 8]

>>> for i in range(len(arr)):
...     for j in range(len(arr[i])):
...             print(arr[i][j], end=' ')
... 
1 2 3 4 5 6 7 8
```

```python
>>> arr = np.array([[ [1,2,3,4],[5,6,7,8]],[[11,12,13,14],[15,1,3,5]]])

>>> print(arr)
[[[ 1  2  3  4]
  [ 5  6  7  8]]

 [[11 12 13 14]
  [15  1  3  5]]]
>>> print(len(arr))
2

>>> print(arr[0])
[[1 2 3 4]
 [5 6 7 8]]
>>> print(len(arr[0]))
2

>>> print(arr[0][0])
[1 2 3 4]
>>> print(len(arr[0][0]))
4

>>> print(arr[0][0][0])
1
>>> print(len(arr[0][0][0]))
TypeError: object of type 'numpy.int64' has no len()
```

```python
>>> arr = np.array([[ [1,2,3,4],[5,6,7,8]],[[11,12,13,14],[15,1,3,5]]])
>>> for i in range(len(arr)):
...     for j in range(len(arr[i])):
...             for k in range(len(arr[i][j])):
...                     print(arr[i][j][k], end="\t")
...             print()
...     print()
... 
1	2	3	4	
5	6	7	8	

11	12	13	14	
15	1	3	5	

>>> for i in range(len(arr)):
...     for j in range(len(arr[i])):
...             for k in range(len(arr[i][j])):
...                     print(arr[i][j][k], end="\t")
...             print()
... 
1	2	3	4	
5	6	7	8	
11	12	13	14	
15	1	3	5
```

___

#### Slicing in Multi Dimensional Arrays


For a 1D array `arrayname[start:stop:stepsize]`

For a 2D array there is  start, stop and step for row and also the columns.
`arr[row_start:row_stop:row_step, col_start:col_stop:col_step]`
`arr[::2, 1:3]` selects every second row and columns 1 to 3.


If no `,` is used, it works only with the rows.
```python
>>> arr = np.array([[1,2,3,4],[5,6,7,8],[10,11,12,13]])
>>> print(arr[0: : ])
[[ 1  2  3  4]
 [ 5  6  7  8]
 [10 11 12 13]]
 
# secects all rows columns
>>> print(arr[ : , : , ])   
[[ 1  2  3  4]
 [ 5  6  7  8]
 [10 11 12 13]]
>>> print(arr[ : 2])  # 0 and 1st rows
[[1 2 3 4]
 [5 6 7 8]]
>>> print(arr[1 : 3]) # 1 and 2nd rows
[[ 5  6  7  8]
 [10 11 12 13]]
>>> print(arr[1:3:2])  # with step 2
[[5 6 7 8]]
```

The columns can be sliced by adding the `,` comma 
```python
>>> arr = np.array([[1,2,3,4],[5,6,7,8],[10,11,12,13]])
>>> # Referring to individual rows

# third row(2) and all columns
>>> print(arr[ 2 , : ])  
[10 11 12 13]

# Second row and all columns
>>> print(arr[ 1 , : ])
[5 6 7 8]

# 1 to last row, all columns by default
>>> print(arr[ 1 : ])
[[ 5  6  7  8]
 [10 11 12 13]]

# 0 row and all columns
>>> print(arr[0:1, : ])
[[1 2 3 4]]
```

The comma is used to separate the range of rows from the range of columns
```python
>>> arr = np.array([[1,2,3,4],[5,6,7,8],[10,11,12,13]])
# 0 row and 0 column slice gives array
>>> print(arr[0:1, 0:1])
[[1]]

# slice of 3rd row, first elment
>>> print(arr[2:3, 0:1 ])
[[10]]

>>> print(arr[2:3, 0 ])
[10]

>>> print(arr[1:2, 1:2 ])
[[6]]

# not an array since no range is given
>>> print(arr[0, 0])
1
```


```python
>>> arr = np.arange(11,36,1)
>>> arr = np.reshape(arr, (5,5))
>>> print(arr)
[[11 12 13 14 15]
 [16 17 18 19 20]
 [21 22 23 24 25]
 [26 27 28 29 30]
 [31 32 33 34 35]] 

>>> arr = np.reshape(np.arange(11,36,1), (5,5))
>>> print(arr)
[[11 12 13 14 15]
 [16 17 18 19 20]
 [21 22 23 24 25]
 [26 27 28 29 30]
 [31 32 33 34 35]]

>>> print(arr[0:2, 0:2])
[[11 12]
 [16 17]]

>>> print(arr[0:2, 0:3])
[[11 12 13]
 [16 17 18]]

>>> print(arr[0:1, 0:3])
[[11 12 13]]

>>> print(arr[2: , 3: ])
[[24 25]
 [29 30]
 [34 35]]
```


Applying stepsize also,    
`arr[row_start:row_stop:row_step, col_start:col_stop:col_step]`
```python
>>> arr = np.reshape(np.arange(11,36,1), (5,5))
>>> print(arr)
[[11 12 13 14 15]
 [16 17 18 19 20]
 [21 22 23 24 25]
 [26 27 28 29 30]
 [31 32 33 34 35]]

# all rows step 1, all columns with step 2
>>> print(arr[ : , : : 2])
[[11 13 15]
 [16 18 20]
 [21 23 25]
 [26 28 30]
 [31 33 35]]

# all rows step 1, all columns step 4
>>> print(arr[ : , : : 4])
[[11 15]
 [16 20]
 [21 25]
 [26 30]
 [31 35]]
 
>>> print(arr[ : , : : 5])
[[11]
 [16]
 [21]
 [26]
 [31]]

>>> print(arr[::2, ::2])
[[11 13 15]
 [21 23 25]
 [31 33 35]]

>>> print(arr[0:4:2, 1:5:2])
[[12 14]
 [22 24]]


# Suitable for 3D array with double comma
>>> print(arr[: , : , : 5])
IndexError: too many indices for array: array is 2-dimensional, but 3 were indexed
```



For **3D Array**: 
```python
arr[ row_start:row_stop:row_step,  col_start:col_stop:col_step, 
			depth_start:depth_stop:depth_step]
```

`arr[:2, 1:3, ::2]` selects the first two rows, columns 1 to 3, and every second element in the depth slices.
