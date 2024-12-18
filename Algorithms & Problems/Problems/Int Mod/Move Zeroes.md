# 283 Move Zeroes #26aug24 

### Problem
```c
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.
Note that you must do this in-place without making a copy of the array.

Example 1:
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]

Example 2:
Input: nums = [0]
Output: [0]

Constraints:
    1 <= nums.length <= 104
    -231 <= nums[i] <= 231 - 1
```
### Trick
```c
Two pointers start together,
One moved by a loop and another manually on a condition.

if the value is not zero, both increment so stay together
if value is zero, only the loop moves forward,
if any value is found, last zero is swapped with this value, the gap between the pointers hold the zeroes,
So any new int will be put in the end of zeroes.

so all zeroes get collected between the pointers and moved towards the end.

changing the starting possition to end can bring an element to the front.

# I had made something very complicated way with placemet, repetative movement but it moved each zero from one end to the other step by step.
Worked but not efficient in time O(n^2)
```
## Code (efficient because it swaps between section of zeroes)
```python
# To take an integer to back
# This is bit like bubbling but just one integer and its copies, no recursion
def swapzeroback(nums):

    left_end = 0
    for right_end in range(len(nums)):

        if nums[right_end] != 0:
            nums[left_end], nums[right_end] = nums[right_end], nums[left_end]
            left_end += 1
    return nums

# If i change the starting point from fron to back, all moves back,
# To bring an integer to front
def swapzeroesfront(nums):

    L = len(nums)-1
    for R in range(len(nums)-1,-1,-1):
    
        if nums[R] != 0:
            nums[L],nums[R] = nums[R], nums[L]
            L -= 1
    return nums
```
### My code (worked but i focused on moving numbers incrementally step by step)
```python
# If i can keep track and swap values between a segment, it will be very efficient

def swapzeroback(nums):
    n = len(nums)

    if n == 1:
        return nums

    write = -1
    for i in range(n-1,-1,-1):
        if nums[i]==0 and i == n-1:
            write -= 1

        if nums[i]==0 and i <n-1:
            for j in range(i, n+write):
                nums[j],nums[j+1] = nums[j+1], nums[j]
            write -= 1

    return nums

# This was to put all zeroes in the front

def swapzerofront(nums):
    write = 0
    
    for i in range(len(nums)):
        if nums[i]==0 and i == 0:
            write += 1

        elif nums[i] == 0:
            for j in range (i, 0+write,-1):
                nums[j] , nums[j-1] = nums[j-1], nums[j]
            write +=1
            
    return nums
```