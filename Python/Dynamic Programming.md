#25aug24 

# Memoization  
Not computing any value again by storing the computed value in a memo table.
Looking up the value before going to compute it again with recursive call.
Storing the values of subproblems in table after computation.

```python
# memoized fibonacci

def fib(n):
	if fibtable[n]:
		return(fibtable[n])
	if n == 0 or n == 1:
		value = n
	else:
		value = fib(n-1) + fib(n-2)
	fibtable[n] = value
	return(value)

# In general

functionf(x,y,z):
	if ftable[x][y][z]:
		return(ftable[x][y][z])
	value = expression in terms of sub problems
	ftable[x][y][z] = value
	return(value)
```

# Dynamic Programming
Anticipate what the memory table looks like
	subproblems are known from problem structure
Solve the subproblems in order of dependency
	solve all the cases that have no dependencies
	then solve the one that have dependency
	dependency must be acyclic to work
	solve the base case first and work up to the value

## Dynamic programming in Fibonacci
```c
# The values of 0 and 1 are stored, other values are built up from there

def fib(n):
	fibtable[0] = 0
	fibtable[1] = 1
	
	for i in range (2,n+1):
		fibtable[i] = fibtable[i-1] + fibtable[i-2]

	return(fibtable[n])
```