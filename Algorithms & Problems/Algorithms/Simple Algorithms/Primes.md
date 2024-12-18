# Factors of n, Checking if Prime, Primes before n
* for a given n, choosing i b/w 1 and n+1 
* n%i == 0 gives factors, appended into a list
* Checking if factors of n are [1,n] only, 
* Iterating over factors of n and checking if prime
* making a separate list 

```python
def factors(n):
    list=[]
    for i in range(1,n+1):
        if n%i==0:
            list.append(i)
    return(list)

def isprime(n):
    return(factors(n) == [1,n])

def primesupto(n):             
    primelist = []
    for i in range (1, n+1):
        if isprime(i):
            primelist.append(i)   # primelist = primelist + [i]
    return(primelist)
```

# Prime or not (direct method)
```python
def prime(n):
	result = True   # consider it a prime
	for i in range(2,n)  # 1 and n are not considered
		if (n % i) == 0:
			result = False   # if any number divides n, its not a prime
			break       # to stop as soon as one divides n
	return (result)
# this is sometime risky, so better to use result to control the loop

def prime(n)
	(result,i) = (True, 2)
	
	while (result and (i<n)):  # if result bocomes False, loop exits
		if (n % i) == 0:       # if i becomes more than n, breaks, both need to be True
			result = False
		i = i+1               # increment every loop so i gets to n
	return (result)
	
```

# Differences of Primes
```python
def prime_diffs(n):
	lastprime = 2    # 2 is the first prime, there is no prime before it
	pd = {}          # dictionary for prime differences
	
	for i in range(3, n+1):
		if prime (i):            # passing i to funtion prime() above
			d = i - lastprime    # find difference b/w last prime found
			lastprime = i        # update last prime

			if d in pd.keys():     # if the difference already exists as key
				pd[d] = pd[d] +1   # update its value by +1
			else:
				pd[d] = 1         # if the difference is unique, create a entry
	return (pd)
	
```
# n Primes
*  since number of iterations unknown, using while loop
* ending loop when items in list = n
* finding factors and checking if it is prime
* appending it to a list
```python
def nprime(n):
    (count,i,primelist) = (0,1,[])
    while count < n:
        if isprime(i):
            primelist = primelist + [i]
            count = count + 1
        i = i + 1     
    return (primelist)
```

# Sum of only primes in a list

*  Iterating over list using 0,1,2.. upto len(l)
* checking if each object in list is prime
* adding each number
```python
def sumprimes(l):
    sum = 0
    for i in range (0,len(l)):
        if isprime(l[i]):
            sum = sum + l[i]
    return(sum)
```