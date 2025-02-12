
To display a right angled triangle with 10 rows
```python
for i in range(1,11):
	for j in range(1, i+1):
		print("* ", end=' ')
	print()
```

```python
for i in range(1,11):
	print( "* "*i )  # repeat * i times
```

```
* 
* * 
* * * 
* * * * 
* * * * * 
* * * * * * 
* * * * * * * 
* * * * * * * * 
* * * * * * * * * 
* * * * * * * * * * 
```


To display a equilateral triangle

```python
n = 40  # to create some space
for i in range(1,11):
	print(' '*n, end='')   # repeat space for n times
	print('* '*i)          # repeat * for n times
	n -= 1
```

```
				* 
			   * * 
			  * * * 
			 * * * * 
			* * * * * 
		   * * * * * * 
		  * * * * * * * 
		 * * * * * * * * 
		* * * * * * * * * 
	   * * * * * * * * * * 
```


To display the numbers in proper format

```python
for x in range(1, 11):
	for y in range(1, 11):
		print( '{:8}'.format(x*y), end='' )
	print()
```

```
   1       2       3       4       5       6       7       8       9      10
   2       4       6       8      10      12      14      16      18      20
   3       6       9      12      15      18      21      24      27      30
   4       8      12      16      20      24      28      32      36      40
   5      10      15      20      25      30      35      40      45      50
   6      12      18      24      30      36      42      48      54      60
   7      14      21      28      35      42      49      56      63      70
   8      16      24      32      40      48      56      64      72      80
   9      18      27      36      45      54      63      72      81      90
  10      20      30      40      50      60      70      80      90     100
```

`{}` is the replacement field and `format()`
`{:8}` represents that the value displays the value `(x*y)` in a field size of 8
So each column size is 8






