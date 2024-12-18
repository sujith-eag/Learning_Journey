# Turning a matrix Left
```
A square nxn matrix of integers can be written in Python as a list with n elements, where each element is in turn a list of n integers, representing a row of the matrix. For instance, the matrix
  1  2  3
  4  5  6
  7  8  9        would be represented as [[1,2,3], [4,5,6], [7,8,9]].

Write a function leftrotate(m) that takes a list representation m of a square matrix as input, and returns the matrix obtained by rotating the original matrix counterclockwize by 90 degrees. For instance, if we rotate the matrix above,
  3  6  9
  2  5  8    
  1  4  7
Your function should not modify the argument m provided to the function rotate().

leftrotate([[1,2],[3,4]])           [[2, 4], [1, 3]]
leftrotate([[1,2,3],[4,5,6],[7,8,9]])       [[3, 6, 9], [2, 5, 8], [1, 4, 7]]
leftrotate([[1,1,1],[2,2,2],[3,3,3]])       [[1, 2, 3], [1, 2, 3], [1, 2, 3]]
```

```python
def leftrotate (m):
    n = len(m)
    r = []

    for _ in range(0,n):
	    r.append([0]*n)  
	    # r = [[0] * n for _ in range(n)] shortcut to make nxn matrix
   
    for i in range (0,n):
        for j in range (0,n):
            r[i][j] = m[j][n-1-i]      # no bracket in bracket r[[] []]
    return (r)


def leftrotate(m):
    size = len(m)
    rotated_m = []

    for i in range(size):
        rotated_m.append([])
        
    for c in range(size-1,-1,-1):
        for r in range(size):
            rotated_m[size-(c+1)].append(m[r][c])
    return(rotated_m)
```