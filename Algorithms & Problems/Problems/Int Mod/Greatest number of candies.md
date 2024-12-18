# 1431 Kids with greatest number of candies #22aug24 
### Question
```c
There are `n` kids with candies. You are given an integer array `candies`, where each `candies[i]` represents the number of candies the `ith` kid has, and an integer `extraCandies`, denoting the number of extra candies that you have.

Return a boolean array `result` of length `n`, where `result[i]` is `true` if, after giving the `ith` kid all the `extraCandies`, they will have the **greatest** number of candies among all the kids, or `false` otherwise.
Note that **multiple** kids can have the **greatest** number of candies.

**Example 1:**
**Input:** candies = [2,3,5,1,3], extraCandies = 3
**Output:** [true,true,true,false,true]

**Example 2:**
**Input:** candies = [4,2,1,1,2], extraCandies = 1
**Output:** [true,false,false,false,false] 

**Example 3:**
**Input:** candies = [12,1,12], extraCandies = 10
**Output:** [true,false,true]
```
### Tip
```
> Find the max of the list using max()
> iterate over the elements of list and add extra and compare with max
> if larger or equal append as True
> if smaller append as False

> There is no need of range() to iterate over a list, it is already a list
```
### Solution
```python
def kidsWithCandies1(candies: list[int], extraCandies: int) -> list[bool]:
    n = extraCandies
    kids = candies
    bolist = []

    for i in range(len(kids)):
        if n + kids[i] >= max(kids):
            bolist.append(True)
        else:
            bolist.append(False)
    return bolist


def kidsWithCandies2(candies: list[int], extraCandies: int) -> list[bool]:
        blist = []
        maximum = max(candies)  # max of list anyway wont change, take beforehand
        
        for child in candies:   # it's a list, no need of len() and range()
            if extraCandies+child >= maximum:
                blist.append(True)
            else:
                blist.append(False)
        return(blist)
  
candies = [2,3,5,1,3]
extraCandies = 3
print( kidsWithCandies2(candies, extraCandies) )
```



