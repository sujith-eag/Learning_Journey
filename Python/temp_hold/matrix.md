
### Initializing a matrix

Shortcuts to make n x n matrix
```python
# 1st
r = [[0] * n for _ in range(n)]

# 2nd
for _ in range(0,n):       
        r.append([0]*n)
```

matrix of 4 x 3,  4 rows 3 columns 
```python
l = [ [0 for i in range(3)]
        for j in range(4)  ]

# the outer (for) is for each row, the inner for is something that is done
#output
	l = [ [0,0,0], [0,0,0], [0,0,0], [0,0,0] ]
```


Wrong method because, each first index got changed as each row is a same list (`zerolist`)
```python
zerolist = [0 for i in range(3)]
l = [ zerolist for j in range(4)]

l[1][1] = 7
l = [0,7,0],[0,7,0],[0,7,0],[0,7,0]
```