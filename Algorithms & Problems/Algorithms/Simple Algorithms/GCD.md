# Greatest Common Divisor

## GCD (normal way)

```python
def gcd(m,n):
	cf = []     # common factors
	for i in range (1, min(m,n)+1):    # only till the smallest value
		if (m % i) == 0 and (n % i) == 0:  # only if it divides both
			cf.append(i)                  # add it to list
	return(cf[-1])                      # return the last one which is GCD

def gcd(m,n):
	for i in range (1, min(m,n)+1):    # no need of list when we just need one value
		if (m % i) == 0 and (n % i) == 0: 
			mrcf = i                  # update the value, 1 is always a divisor
	return(mrcf)       

# this takes time proportional to min(m,n)
```

Understanding GCD
```
d divides m & n
m = ad, n = bd
m - n = (a - b)d 
d also divides (m-n)
so passing (n, m-n) as argument gives GCD 
this is worse in efficiency, max(m,n)
```

```python
def gcd (m,n):
	(a,b) = ( max(m,n), min(m,n))
	
	if a % b == 0:     # base case, b is gcd
		return(b)
	else:
		return( gcd(b,a-b) )
```


## GCD (Euclid's Algorithm)

To find Greatest common divisor
	For given numbers x and y,  x>y
	if x%y == 0,     then y is the gcd
	when x%y != 0,        then the gcd of reminder r is equal to gcd of (x, y)
	so gcd is found for (y, r)

Since r is always smaller than x and y, no need to arrange using min and max or swap.
If there exists no gcd, then it will reach 1 and 1 will be returned as gcd.

Time is proportional to number of digits in a max(m, n)     for 5 digit number, it is 5

```python
def gcd(x,y):
if x>y:
		(x,y)=(y,x)      # arranging min and max

	if x % y == 0
		return(y)
	else:
		return( gcd(y,x%y))     # Using Recursion 
```

```python
def gcd(x,y):              # Using While Loop
	if x>y:
		(x,y)=(y,x)
	
	while x%y!=0           # when there is a reminder enter loop and change values
		(x,y) = (y,x%y)

	return(y)              # No reminder, exit loop, return the smalles value 
```