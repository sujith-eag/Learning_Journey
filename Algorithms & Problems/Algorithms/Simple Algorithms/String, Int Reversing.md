# To Reverse a String
`Iterate over the string with for till length of string from 1 get the -i object from a string and append to a new string`
```python
def str_reverse (s):
	reverse = ""
	for i in range (1,len(s)):
		letter = l[-i]       # reverse = reverse + l[-i]
		reverse = reverse + letter
	return(reverse)
```

# To Reverse an Int
Divide number by 10, 
Reminder will be the last number, Quotient will be rest.
Increase the power of new no by multiplying by 10, add reminder
Divide the quotient similarly till the quotient becomes 0
When quotient is 0, while loop ends
(i can also convert it into a string and reverse the order and join it to make int)

```python
def intreverse(n):
	rev = 0
	while n>0:
		(n,r) = (n//10, n%10)
		rev = rev*10 + r
	return(rev)
```