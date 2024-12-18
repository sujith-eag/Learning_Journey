# Example 1:

**Input:** height = [1,8,6,2,5,4,8,3,7]
**Output:** 49
**Explanation:** The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

**Example 2:**
**Input:** height = [1,1]
**Output:** 1

**Constraints:**
- `n == height.length`
- `2 <= n <= 105`
- `0 <= height[i] <= 104`



```
# Reversing a list

def mystery(l):
    if l == []:
        return(l)
    else:
        return(mystery(l[1:])+l[:1])
        
mystery([22,14,19,65,82,55])
```

```
pairs = [ (x,y) for x in range(4,1,-1) for y in range(5,1,-1) if (x+y)%3 == 0 ]

All pairs (i,j) with i ∈ {4,3,2}, j ∈{5,4.3,2} such that i + j is a multiple of 3
```

```
wickets = {
	"Tests":{"Bumrah":[3,5,2,3],"Shami":[4,4,1,0],"Ashwin":[2,1,7,4]},
	"ODI":{"Bumrah":[2,0],"Shami":[1,2]}
	}

wickets["ODI"]["Ashwin"] = [4,4]
# direct assignment to a new key adds a value.
```


```
- Write a Python function frequency(l) that takes as input a list of integers and returns a pair of the form (minfreqlist,maxfreqlist) where
    
    - minfreqlist is a list of numbers with minimum frequency in l, sorted in ascending order
    - maxfreqlist is a list of numbers with maximum frequency in l, sorted in ascending order

frequency([13,12,11,13,14,13,7,11,13,14,12])
    ([7], [13])    

frequency([13,12,11,13,14,13,7,11,13,14,12,14,14])
    ([7], [13, 14])

frequency([13,12,11,13,14,13,7,11,13,14,12,14,14,7])
    ([7, 11, 12], [13, 14])

frequency([1,2,3,4,5,5,4,3,2,3,4,5,5,4,5])
	([1], [5])
	
frequency([4,4,4,1,1,2,2,2,3,3])
	([1, 3], [2, 4])|

frequency([1,1,1,1,1])
	([1], [1])
frequency([17322,271898,374,374,374,423432423,423432423,423432423,423432423,5325,5325,5325,5325,5325])
	([17322, 271898], [5325])

frequency([17322,374,17322,374,17322,374])
	([374, 17322], [374, 17322])

frequency([9842])
	([9842], [9842])
frequency([-17322,-271898,-374,-374,-374,-423432423,-423432423,-423432423,-423432423,-5325,-5325,-5325,-5325,-5325])
	([-271898, -17322], [-5325])

frequency([-17322,-374,-17322,-374,-17322,-374])
	([-17322, -374], [-17322, -374])
```

```
- An airline has assigned each city that it serves a unique numeric code. It has collected information about all the direct flights it operates, represented as a list of pairs of the form (i,j), where i is the code of the starting city and j is the code of the destination.
    
    It now wants to compute all pairs of cities connected by one intermediate hope — city i is connected to city j by one intermediate hop if there are direct flights of the form (i,k) and (k,j) for some other city k. The airline is only interested in one hop flights between different cities — pairs of the form (i,i) are not useful.
    
    Write a Python function onehop(l) that takes as input a list of pairs representing direct flights, as described above, and returns a list of all pairs (i,j), where i != j, such that i and j are connected by one hop. Note that it may already be the case that there is a direct flight from i to j. So long as there is an intermediate k with a flight from i to k and from k to j, the list returned by the function should include (i,j). The input list may be in any order. The pairs in the output list should be in lexicographic (dictionary) order. Each pair should be listed exactly once.
    
    Here are some examples of how your function should work.
    
     
onehop([(2,3),(1,2)])        [(1, 3)]
    
onehop([(2,3),(1,2),(3,1),(1,3),(3,2),(2,4),(4,1)])
    [(1, 2), (1, 3), (1, 4), (2, 1), (3, 2), (3, 4), (4, 2), (4, 3)]
    



onehop([(1,2)])      []

onehop([(1,2),(2,1)])     []
onehop([(1,2),(3,4)])     []

onehop([(1,2),(3,4),(5,6)])  []

onehop([(1,2),(2,1),(3,4),(4,3)])      []

onehop([(1,3),(1,2),(2,3),(2,1),(3,2),(3,1)])
	[(1, 2), (1, 3), (2, 1), (2, 3), (3, 1), (3, 2)]

onehop([(1,2),(2,3),(3,4),(4,5),(5,1)])
	[(1, 3), (2, 4), (3, 5), (4, 1), (5, 2)]

onehop([(1,2),(2,3),(3,4),(4,5),(5,1),(5,6),(6,7),(7,8),(8,9),(9,5)])
	[(1, 3), (2, 4), (3, 5), (4, 1), (4, 6), (5, 2), (5, 7), (6, 8), (7, 9), (8, 5), (9, 1), (9, 6)]

onehop([(1, 2), (1, 3), (1, 4), (1, 5), (1, 6), (1, 7), (1, 8), (1, 9), (2, 1), (2, 3), (2, 4), (2, 5), (2, 6), (2, 7), (2, 8), (2, 9), (3, 1), (3, 2), (3, 4), (3, 5), (3, 6), (3, 7), (3, 8), (3, 9), (4, 1), (4, 2), (4, 3), (4, 5), (4, 6), (4, 7), (4, 8), (4, 9), (5, 1), (5, 2), (5, 3), (5, 4), (5, 6), (5, 7), (5, 8), (5, 9), (6, 1), (6, 2), (6, 3), (6, 4), (6, 5), (6, 7), (6, 8), (6, 9), (7, 1), (7, 2), (7, 3), (7, 4), (7, 5), (7, 6), (7, 8), (7, 9), (8, 1), (8, 2), (8, 3), (8, 4), (8, 5), (8, 6), (8, 7), (8, 9), (9, 1), (9, 2), (9, 3), (9, 4), (9, 5), (9, 6), (9, 7), (9, 8)])

[(1, 2), (1, 3), (1, 4), (1, 5), (1, 6), (1, 7), (1, 8), (1, 9), (2, 1), (2, 3), (2, 4), (2, 5), (2, 6), (2, 7), (2, 8), (2, 9), (3, 1), (3, 2), (3, 4), (3, 5), (3, 6), (3, 7), (3, 8), (3, 9), (4, 1), (4, 2), (4, 3), (4, 5), (4, 6), (4, 7), (4, 8), (4, 9), (5, 1), (5, 2), (5, 3), (5, 4), (5, 6), (5, 7), (5, 8), (5, 9), (6, 1), (6, 2), (6, 3), (6, 4), (6, 5), (6, 7), (6, 8), (6, 9), (7, 1), (7, 2), (7, 3), (7, 4), (7, 5), (7, 6), (7, 8), (7, 9), (8, 1), (8, 2), (8, 3), (8, 4), (8, 5), (8, 6), (8, 7), (8, 9), (9, 1), (9, 2), (9, 3), (9, 4), (9, 5), (9, 6), (9, 7), (9, 8)]
```

```python
def frequency(l):
    count = {}
    for n in l:
        if n in count.keys():
            count[n] = count[n]+1
        else:
            count[n] = 1
    minlist = findmin(count)
    maxlist = findmax(count)
    return((minlist,maxlist))

def findmin(d):
    upperbound = 0
    for n in d.keys():
        if d[n] > upperbound:
            upperbound = d[n]

    minlist = []
    mincount = upperbound

    for n in d.keys():
        if d[n] < mincount:
            minlist = [n]
            mincount = d[n]
        elif d[n] == mincount:
            minlist.append(n)
    return(sorted(minlist))

            
def findmax(d):
    maxlist = []
    maxcount = 0

    for n in d.keys():
        if d[n] > maxcount:
            maxlist = [n]
            maxcount = d[n]
        elif d[n] == maxcount:
            maxlist.append(n)
    return(sorted(maxlist))

def onehop(l):
    direct = {}
    for (i,j) in l:
        if i in direct.keys():
            direct[i].append(j)
        else:
            direct[i] = [j]

    hopping = []

    for src in direct.keys():
        for dest in direct[src]:
            if dest in direct.keys():
                for remote in direct[dest]:
                    if src != remote:
                        hopping.append((src,remote))

    return(remdup(sorted(hopping)))
            
def remdup(l):
    if len(l) < 2:
        return(l)

    if l[0] != l[1]:
        return(l[0:1]+remdup(l[1:]))
    else:
        return(remdup(l[1:]))
```