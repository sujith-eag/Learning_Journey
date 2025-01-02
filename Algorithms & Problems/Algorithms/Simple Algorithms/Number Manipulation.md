## Algorithm to identify Perfect Squares

'//' divides the number and rounds it to nearby number, 7 // 3 == 2   15 // 2 == 7
The function f(n) returns True when there is one divisor that i * i=n,  
	so n/i == i,  4/2=2 , 9/3=3, 16/4=4
Its true if and only if n is a perfect square, The output is true if s%2 == 1,
**** still i don't know how 1%2 == 1

```python
def f(n):
	s=0
	for i in (2,n+1)
		if n//i==i and n%i==0:     # Checking if there is i*i=n
			s = 1                  # Assigning an odd number

	return(s%2 == 1)               # Checking if the number is odd
```

## Algorithm for Finding Factorial of n
n! = n (n-1) (n-2)....1
n! = n (n-1)!               this is what is being used

```python
def factorial (n):
    if n <= 0:
        return(1)
    else:
        val = n* factorial(n-1)
        return(val)
```


## To find nC2 = n!/(n-r)!r!
For a Non negative number n, add n-1, add n-2 so on till n == 0.  Recursive call ends as 0 is return.
The problems of finding unique handshakes or lines formed

```python
def factorial(n):
    if n==0:
        return(0)
    else:
        return(n + factorial(n-1))  #Recurcively adding no 1 less than n till 0 
```
