# To find Matching signs () {} 

```
Get a string.
Iterate over string, with for loop using str length.
if "(" is found increment a value, if ")" is found decrement the value. 
Return false if value is < or > 0.
Return value if == 0
(There was another way of using a dict, key and value to compare)
```
```python
def matched(x)
	tally = 0
	for i in range (0,len(x)):
		if x[i] == "(":
			tally = tally +1
		elif x[i] == ")"
			tally = tally -1
	if tally < 0 or tally >0:
		return(False)
	return(tally==0)     # return(True)
```