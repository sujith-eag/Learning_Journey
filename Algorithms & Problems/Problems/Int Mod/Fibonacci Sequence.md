
A sequence in which any number is a sum of the two numbers before it  
n = 1, 1, 2, 3, 5, 8, 13, 21, 34, . . .   

General formula would be:  ***fib(n) = fib(n-1) + fib(n-2)***

# Print (n)th Fibonacci number

Version 1 (Base case, recursion)
```python
def fibinachi(n):
    if n < 2:
        return(n)
    else:
        return(fibinachi(n-1)+fibinachi(n-2))

n = int(input("Fibinachi of..  "))
print(fibinachi(n))
```

Importance of base case, to have a certain limit or answer at end of the branching recursion from where it can come back.

If `n < 2`, that is 0 or 1, will return 0 and 1. end of function.   
If `n = 2`,  its `n-1` will return 1,   
If its `n - 2` will return 0,  so 1+0 will be 1,   

Without `if n<2: return (n)`,  there is no end to recursion as no answer is returned up.   

#### Limitation of recursion, 
Exponential run time, for each call there will be 2 more calls and so on.   
So it grows exponentially.

9 calls for 4th element,  15 for 5th,  177 for 10th,  21891 for 20th.   
__________

# To print n Fibonacci numbers

### Version 2 (Memorization)
```python
from typing import Dict
memo: Dict[int, int] = {0: 0, 1: 1} # our base cases

def fibinachi(n):
    if n not in memo:
        memo[n] = fibinachi(n - 1) + fibinachi(n - 2) # memoization
    return memo[n]
print(fibinachi(50))  
```

### Automatic memorization
```python
from functools import lru_cache
@lru_cache(maxsize=None)

def fib4(n: int) -> int: # same definition as fib2()
	if n < 2: # base case
		return n
	return fib4(n - 2) + fib4(n - 1) # recursive case

if __name__ == "__main__":
	print(fib4(5))
	print(fib4(50))
```

Python has a built-in decorator for memorizing any function automagically.    
In `fib4()`, the decorator `@functools.lru_cache()` is used.    
Each time `fib4()` is executed with a novel argument, the decorator causes the return value to be cached.     
Upon future calls of `fib4()` with the same argument, the previous return value of `fib4()` for that argument is retrieved from the cache and returned.    

`@lru_cache’s` `maxsize` property indicates how many of the most recent calls of the function it is decorating should be cached.    
Setting it to `None` indicates that there is no limit.    


# For Loop with some idea
 Version 3

```python
def fibinachi(n):
    if n == 0:
        return n
    else:
        last = 0
        next = 1
        for _ in range (1,n):
            last, next = next, next+last
        return(next)

n = int(input("number of digits  "))  # my way
print(fibinachi(n))


if __name__ == "__main__":    # standard way
	print(fib5(5))
	print(fib5(50))
```
Working forward, from 0 and 1 towards nth number using for loop, bit of a overly smart way, it takes n-1 steps to arrive at the answer.

# printing all values upto nth number

 generator (yield statement)

```python  
def fibinachi(n):
    yield 0  # special case
    if n>0:
        yield 1  # special case
  
    last = 0
    next = 1
    for i in range(1,n):
        last, next = next, last + next
        yield next   # main generation step

for i in fibinachi(50):
    print(i)
```

If `fib6.py` is run, you will see 51 numbers in the Fibonacci sequence printed. 
For each iteration of the for loop for `i` in `fib6(50):`, 
`fib6()` runs through to a yield statement. 
If the end of the function is reached and there are no more yield statements, the loop finishes iterating.