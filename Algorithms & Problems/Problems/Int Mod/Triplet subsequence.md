# 334 Increasing Triplet subsequence #25aug24
## Problem
```c
Given an integer array nums, return true if there exists a triple of indices (i, j, k) such that i < j < k and nums[i] < nums[j] < nums[k]. If no such indices exists, return false.

Example 1:
Input: nums = [1,2,3,4,5]
Output: true
Explanation: Any triplet where i < j < k is valid.

Example 2:
Input: nums = [5,4,3,2,1]
Output: false
Explanation: No triplet exists.

Example 3:
Input: nums = [2,1,5,0,4,6]
Output: true
Explanation: The triplet (3, 4, 5) is valid because nums[3] == 0 < nums[4] == 4 < nums[5] == 6.
```

```c
nums = [1,2,3,4,5]  # T
nums = [2,1,5,0,4,6]  # T
nums = [20,100,10,12,5,13]  # T
nums = [5,4,3,2,1] # F
nums = [6,7,1,2]   # F
nums = [0,4,2,1,0,-1,-3]  # F
nums = [5,1,6]      # F
```

## New Insights
```c
> just using a counter doesnt work, while simply checking one element and the next element, there will be mistakes as the previous lows and highs will be looked over.
> The first approach i thought only consequitive numbers are valid (very easy to do) but no, can be anywhere in the list.
> Each Test cases above put up differnt challenges and showed why my 'counter set and reset' 'min' 'min max' approaches failed

> The right approach was saving the 'first' 'second' numbers, if any other number is larger than this, then True.
> Problem was assigning "place holder value to an int" like 'first' 'second'
> Lists are easy, but using 0, 1, -1 doesnt work in many cases.

> float("inf") represents 'positive infinity'.
> float("-inf")  'negative infinity' for finding max values
> value = None   not for comparision and numbers
> very useful for initializing numbers while looking for min and max value comparisions.

> again if, elif and else track to check and pass values seqientially,
> This > < >= <= still needs some understanding, the more i think about it the more confusing it seems.
```
```python
	min_value = float('inf')
	for x in iterable:
	    if x < min_value:
	        min_value = x
	
	max_value = float('-inf')
	for x in iterable:
	    if x > max_value:
	        max_value = x
```
## Code
```python
def increasingTriplet(nums):
	if len(nums) < 3:     # Base 1
        return False
        
    first, second = float("inf"), float("inf")  # largest place holder
    
    for num in nums:
        if num <= first:    # smallest num gets assigned first
            first = num
            
        elif num <= second: # next largest number is second
            second = num

        else:       # if there is one more, then triplet is True
            return True
            
    return False
```
### 90% success (counter approach)
```
# There was another first version that didnt use any min value, just counter
# That worked 80% of cases

def increasingTriplet(nums: List[int]) -> bool:
        seq = 0
        n = len(nums)
        min = nums[0]

        for i in range(n):
            if i == n-1:
                return False
            elif min < nums [i+1]:
                seq += 1
                if seq == 2:
                    return True
            else:
                min = nums[i]
```