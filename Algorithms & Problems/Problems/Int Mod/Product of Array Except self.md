# 238 Product of Array except self #24aug24 
## Problem
```c
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer. You must write an algorithm that runs in O(n) time and without using the division operation.

Example 1:
Input: nums = [1,2,3,4]
Output: [24,12,8,6]

Example 2:
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```

```c
# First attempt 
Using a temporary variable hold value to remove it from the list but not loose the value, simultaneous swapping saves time.

# Using division and handling edge cases(zeros)
Zeroes in products make things very easy, so count all zeroes
Taking product of all numbers and dividing by any number removes it. so take the product of all elements.(both happen in onle run)

Next to check all base case of, >1 zeroes, 1 zero, and no zeroes in next go.
so ends in two runs
```
### The New method / Lot of new lessons
```c
# Prefix and suffix of any number!! need to understand what is happening
# Ok, lot of new things to pick on

- Base Logic
- if the multiples of all prefixes and sufixes are multiplied, gives the required product for the number without the number in it.

- New tricks
- [1,   2,   3,  4,  5,  6]    Int list
- [-,   1,   2,  6,  24, 120]   Prefixes
- [720,360, 120, 30,  6,  -]    Sufixes
- [720,360, 240, 180, 144, 120]  Result
- Few things, 1 has no prefix, 6 has no suffix so in there place a place filler 1

To create this effect, so many new things
> To have one element in list before any value gets appended,
> One place blank in beginning, Using first element to go into second place and ignoring the last result.
> in suffix, iterating from end and updating the values also from the end.
> So append doesnt work, list[] declararion doesnt work, usual assignment doesnt work, even multipying way also doesnt.
```
## Pseudocode
```c
> Make lists for prefix, suffix, results
> have temp value holders for prefix and suffix to increment with products
> iterate over list and make lists (check code)
> multiple of prefix and suffix makes the result.
> Could have added base checks for zeroes, but requires 3 more rounds making it less efficient
```
## Code (First attempt without division operator)
```python
def factormul(l):
    ml = []          # make new list
    a,b = 1,1       # 2 factors for holding values temporarily
    
    for i in range(len(l)):
        l[i],a = a,l[i]   # move value to a, and take up 1
        for j in range(len(l)):
            b = l[j]*b    # multily all values, store it in b
        ml.append(b)      # append value to list
        b = 1             # turn back the value of b to 1
        l[i], a = a, l[i] # return value of element from a, repeat for all values
        
    print(ml)
```
### Code (with division and base case of zeroes)
```python
def multiplefact(l):
    nl = []
    zeroes = 0
    product = 1

    if len(l) == 0:    # base 1, no elements
        return []
        
    for num in l:
        if num == 0:
            zeroes += 1
        else:
            product *= num
            
    for i in range(len(l)):
        if zeroes > 1:   # base 2, all multiples will be zeroes
            nl.append(0)
        elif zeroes == 1: # base 3, only one is will have value
            if l[i] == 0:
                nl.append(product)
            else:        
                nl.append(0)
        else:
            m = product//l[i]  # actual, each one has a value
            nl.append(m)

    print(nl)
```
### Code (tracking prefix and suffix multiples) 
```python
# I got it now, good new tricks

def multiplefact(nlist):
    n = len(nlist)
    prefix = [1]*n   # assignment cannot happen to empty list, only append can
    suffix = [1]*n   # to assign at any place, list should have n number of elements
    result = [0]*n   # No need of multiplying, direct assignment
    
    pre = 1
    for i in range(n):
        prefix[i] = pre  # assignment in list before hand in first place
        pre *= nlist[i]  # storing value of first element to assign later
                         # last value having all multiples is discarded

    suf = 1
    for i in range(n-1, -1, -1): # last element to first, -1 decremental
        suffix[i] = suf   # value assigned to last place in list
        suf *= nlist[i]  # the n-1 th element doesnt have suffix
        
    for i in range(n):
        result[i] = prefix[i]*suffix[i]
    print(result)


nums = [-1,1,0,-3,3,12,4,5,-1]
multiplefact(nums)

nums = [1,2,3,4,5,6]
multiplefact(nums)

nums = [-1,1,0,-3,3,12,4,5,0]
multiplefact(nums)
```
