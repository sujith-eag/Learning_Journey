# Decreasing Sequence
### Question
```
Write a function contracting(l) that takes as input a list of integer l and returns True if the absolute difference between each adjacent pair of elements strictly decreases.
  
contracting([9,2,7,3,1])    True
contracting([-2,3,7,2,-1])  False
contracting([10,7,4,1])     False
```

```
No need to check if everything is increaasing, if one decreases its False

need to compare difference of 1st 2nd with 2nd 3rd, can be done by adding 0,1,2
    should run (n-3) loop so range b/w (0,n-2)   (otherwise goes out of index)
    abs() should be used to get absolute value
if even one is less than or equal, return False
otherwise for loop can end, return True

Edge case is differences are equal, not allowed.  if n<3 not allowed
```

```python
def contracting(l):
    n = len(l)
    if n < 3:
        return False
        
    for i in range(0,n-2):
        if ( abs(l[i] - l[i+1]) <= abs( l[i+1] - l[i+2]) ):
            return False
    return True



def contracting_iterative(l):
    if len(l) < 3:
        return(True)

    for i in range(len(l)-2):
        diff = abs(l[i+1]-l[i])
        if diff <= abs(l[i+2]-l[i+1]):
            return(False)
    return(True)


# Recursive Method
def contracting(l):
    if len(l) < 3:
        return(True)

    return((abs(l[1]-l[0]) > abs(l[2]-l[1])) and contracting(l[1:]))
```
