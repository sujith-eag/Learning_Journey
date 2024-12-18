# Hill and Valley
```
In a list of integers l, the neighbours of l[i] are l[i-1] and l[i+1].
l[i] is a hill if it is strictly greater than its neighbours and a valley if it is strictly less than its neighbours.

Write a function counthv(l) that takes as input a list of integers l and returns a list [hc,vc] where hc is the number of hills in l and vc is the number of valleys in l.

counthv([1,2,1,2,3,2,1])    [2, 1]
counthv([1,2,3,1])          [1, 0]
counthv([3,1,2,3])          [0, 1]
```

```python
def counthv(l):
    n = len(l)
    peak = 0
    valley = 0

    if n < 3:
        return [0,0]
               # should start from 1 end at n-2 (0 & len(l) wont have l & r)
    for i in range (1,n-1):       # If middle is less than r and l, valley

        if l[i] < l[i-1] and l[i] < l[i+1]:
            valley = valley+1
# If both are smaller than middle, mountain
        if l[i] > l[i-1] and l[i] > l[i+1]:
            peak = peak+1
    return [peak,valley]


def counthv(l):
    hills = 0
    valleys = 0
    for i in range(1,len(l)-1):
        if l[i] > l[i-1] and l[i] > l[i+1]:
            hills = hills + 1
        if l[i] < l[i-1] and l[i] < l[i+1]:
            valleys = valleys + 1
    return([hills,valleys])
```
