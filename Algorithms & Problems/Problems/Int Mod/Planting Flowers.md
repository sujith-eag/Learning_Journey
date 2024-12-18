# 605 Planting Flowers #23aug24
## Question
```c
You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in **adjacent** plots.
Given an integer array `flowerbed` containing `0`'s and `1`'s, where `0` means empty and `1` means not empty, and an integer `n`, return `true` _if_ `n` _new flowers can be planted in the_ `flowerbed` _without violating the no-adjacent-flowers rule and_ `false` _otherwise_.

**Example 1:**
**Input:** flowerbed = [1,0,0,0,1], n = 1
**Output:** true

**Example 2:**
**Input:** flowerbed = [1,0,0,0,1], n = 2
**Output:** false
```
### Test cases
~~~c
flowerbed = [1,0,0,0,1,0,0]
n = 2  #True
print(canPlaceFlowers(flowerbed,n))
  
flowerbed = [1,0,0,0,1]
n = 1  # True
print(canPlaceFlowers(flowerbed,n))

flowerbed = [1,0,0,0,1]
n = 2 # False
print(canPlaceFlowers(flowerbed,n))

flowerbed = [1,0,0,0,0,1]
n = 2  # False
print(canPlaceFlowers(flowerbed,n))

flowerbed = [1,0,0,0,0,0,1]
n = 3  # False
print(canPlaceFlowers(flowerbed,n))

flowerbed = [0,1,0]
n = 1      # False
print(canPlaceFlowers(flowerbed,n))
~~~

## Clues
```c
> Use a paper and pen to plan first

> Find the unique or unlikely cases,(n=0, len(list)=1) Eliminate them in beginning

> Collect all the edge cases first and see how to handle them first. 
  (in 0th element, i+1 has to be checked, in n-1th element i-1 has to be checked) otherwise it causes Outofbound IndexError.

>Always better to do any increment at once rather than many places causing error

>Sometime while loop is better when manual increment might be done. 
  (but conditions can be made similar to for loop using a counter)

> Using 'continue' to skip all the steps below saves so many steps when there is nothing more to be done like, list[i]==1. If it doesnt skip then it is 0. 

> Properly distinguishing between if, elif and else. All if doesnt always work well when previous ones have already workd and checking again with next conditions might cause errors.

> using or, and makes the code more compact but sometimes not very clear.

>  If there is a need to check index for edge cases, then 'for i in list' not the ideal way to go even though it makes cheking easy.


> Check that the previous plot is either out of bounds or also 0 (i.e., the plot to the left is empty or it's the beginning of the list).
> Check that the next plot is either out of bounds or also 0 (i.e., the plot to the right is empty or it's the end of the list).
```
## Pseudocode
```c
Pseudocode

if len[l] = 1, 
	check if [0] is 0 and n=0 or 1  i.e  return(list[0]==0 and n<=1)
if n = 0, no need to check, return True

using while loop or for loop to iterate,
if list[i]==1, no need of action, increment iteration
else, list[i] is 0,
	three cases,
	if i==0, check only right side,
	elif i==len(list)-1, check only left
	elif both not the case, then its a middle one, check left and right

	 if conditons satisfy, change the possition [i] to 1
	 check if planted = n, if so end by returning True
		 if not, that place is filled, there is no need to check the next one, skip over and repeat the loop till all elements are checked.

	at end of loop, return False or ( planted >= n)
```

## Most of the Attempts
### Final Versions
```python
# Final version with While loop

def canPlaceFlowers(flowerbed: list[int], n: int) -> bool:
	bed = flowerbed
	m = len(bed)
    planted = 0

    if n == 0:
        return True
    if m == 1:
        return (bed[0] == 0 and n<=1 )
        
    i = 0
    while i < m:
        if bed[i] == 1:
            i += 1  # move on
            continue

        if (i==0 and bed[i+1] == 0) or (i == m-1 and bed[i-1] == 0) or 
									        (bed[i-1]==0 and bed[i+1]==0):
            bed[i] = 1
            planted += 1
            i += 1  # skipping next place
  
        if planted >= n:
            return True
        i += 1  # to increment in while loop            


    return (planted>=n)
```
```python

# Final version with For loop

	def canPlaceFlowers(flowerbed: list[int], n: int) -> bool:
        bed = flowerbed
        m = len(bed)
        planted = 0

        if n == 0:
            return True
        if m == 1:
            return (bed[0] == 0 and n<=1 )
        
        for i in range(m):
            if bed[i]==1:
                continue
  
            if (i==0 and bed[i+1] == 0) or (i == m-1 and bed[i-1] == 0) or
						             (bed[i-1]==0 and bed[i+1]==0):
                bed[i] = 1
                planted += 1
  
            if planted >= n:
                return True
            i += 1
  
        return (planted>=n)
```

```python
# Using While loop (This is GPT, im not clear on the checking conditions)

def canPlaceFlowers(flowerbed: list[int], n: int) -> bool:
    count = 0      # To count the number of flowers planted
    i = 0          # Index to traverse the flowerbed

    while i < len(flowerbed):
        if flowerbed[i] == 0:  
            if (i == 0 or flowerbed[i - 1] == 0) and 
	            (i == len(flowerbed) - 1 or flowerbed[i + 1] == 0):
                flowerbed[i] = 1  # Plant a flower
                count += 1
        i += 1    
    return count >= n
```
### Testing Grounds
```python
	def canPlaceFlowers(flowerbed: list[int], n: int) -> bool:
        bed = flowerbed
        m = len(bed)
        planted = 0
  
        if n == 0:
            return True
        if m == 1:
            return (bed[0] == 0 and n<=1 )
        
        for i in range(m):
            if bed[i]==1:              # if 1, skip rest of the checks
                continue

            elif i==0 and bed[i+1] == 0:    # checking edge cases, is it first
                bed[i] = 1
                planted += 1
            elif i == m-1 and bed[i-1] == 0:    # is it last
                bed[i] = 1
                planted += 1
            elif bed[i-1]==0 and bed[i+1]==0:   # if not those, then it is the middle
                bed[i] = 1
                planted += 1
  
            if planted >= n:
                return True
            i += 1

        return (planted>=n)
```
#### 
```python
# if i take, for i in bed:  i wont be able to check index. for range will handle the end
# i==0 and i == end happens once, never together
# checking i+1 is for 0, and i-1 is for end.
# if i==0 and [i+1]==0, plant
# if i==end and [i-1]==0, plant (incrementing i will end loop)
# if [i+1]==0 and [i-1]==0, plant

	def canPlaceFlowers(flowerbed: list[int], n: int) -> bool:
        bed = flowerbed
        m = len(bed)
        planted = 0

        if n == 0:
            return True
        if m == 1:
            return (bed[0] == 0 and n<=1 )

        for i in range(m):
            if bed[i] == 0:
                if i==0 and bed[i+1] == 0:         # checking edge cases first
                    bed[i] = 1
                    planted += 1
                elif i == m-1 and bed[i-1] == 0:
                    bed[i] = 1
                    planted += 1
                elif bed[i-1]==0 and bed[i+1]==0:   # here out of bound is happening for looking at i+1
                    bed[i] = 1                      # just make sure its not executed simple, elif saves the code
                    planted += 1
  
                if planted >= n:
                    return True
  
        return (planted>=n)
```
#### Second own implementation that failed, too complicated also, what is happening here?
```python
def canPlaceFlowers(spots, n):
    end = len(spots)-1
    planted = 0

    if n == 0:
        return True
        
    for pos in range(end+1):
        if spots[pos] == 0:
  
            if pos == 0:
                if spots[pos+1] ==0:
                    spots[pos] = 1
                    planted += 1

            elif pos == end:
                if spots[pos-1] == 0:
                    planted += 1
                    return(planted>=n)
                else:
                    return False
                    
            elif spots[pos-1] == 0 and spots[pos+1]==0:
                planted += 1
  
        if spots[pos] == 1:
            if pos == end:
                return(planted>=n)
  
    return (planted>=n)
```
#### Code that worked 90% (with very wrong plan)
```python
def canPlaceFlowers(flowerbed: list[int], n: int) -> bool:
        extra_zeroes = 0
  
        for i in flowerbed:
            if i == 1:
                extra_zeroes += -1
            if i == 0:
                extra_zeroes += 1

        if extra_zeroes%2==0:
             return (extra_zeroes/2 >= n)
        else:
             return((extra_zeroes+1)/2 >= n)
```


