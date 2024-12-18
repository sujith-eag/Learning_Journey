#24aug24 

# 541 Reverse String II 

```c
Given a string 's' and an integer 'k', reverse the first 'k' characters for every '2k' characters counting from the start of the string.

If there are fewer than 'k' characters left, reverse all of them. 

If there are less than '2k' but greater than or equal to 'k' characters, 
then reverse the first 'k' characters and leave the other as original.

Example 1:
Input: s = "abcdefg", k = 2
Output: "bacdfeg"

Example 2:
Input: s = "abcd", k = 2
Output: "bacd"
```
### Tips & Discovery
```c
Pseudocode
> convert to list, get len of list for range
> iterate at 2*k length in the loop, forming 'starting pointer'
> k+start forms the end pointer, (0+k, 2*k+k, 4*k+k) where swap needs to happen
> if k=2, start will be at (o,4,8,..)  end will be at (2,6,10)
> take slice of elements b/w start and end, swap them using new tool [::-1]
> re assign it to the section in the list
> To Deal with last bit, take 'min(start,n)' so when start goes beyond len of list, n will become end point, so remaining elements get swapped.


* list[::-1]   list[a:b][::-1]   list( l[s] )[::-1]   just this can reverse the list so easily

* lisp[start:end] = lisp[start:end][::-1]
* This didnt go well in beginning, on how a new slice is merged into larger list but it seems it is just re assigning the reversed list into "just that section" of the large list so the list is intact. (unintuitive but works)

* Taking min(m,n) in a range for loop with iteration that can go beyond the range of list so when that happens, the pointer stops at the last no even if it doesnt satisfy the increment.
* So very nice in handeling last section edge cases
```
### Code
```python
def kswap(s,k):
    lisp = list(s)
    n = len(lisp)

    for start in range (0, n, 2*k):
        end = min( start+k, n )
        lisp[start:end] = lisp[start:end][::-1]
    return( "".join(lisp))



s = "abcdefg"
k = 2
print(kswap(s,k))

s = "abcd"
k = 2
print(kswap(s,k))
```
