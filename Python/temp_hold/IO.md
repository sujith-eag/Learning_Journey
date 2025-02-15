
print(" The first line \n next line \t with tab space")

`print( 'hai'*3) `

Formatted string statement
```python
>>> x = 10
>>> print( "value = %i" % x ) 
value = 10

>>> x, y = 10, 15
>>> print( "value: x =  %i, y = %i" % (x, y) ) 
value: x =  10, y = 15
```
`%s` is for formatted string,  `%20s`  `%-20s` aligns left right with 20 spaces
`%f ` is for floating point  `%.3f` means 3 precison, `%3.3f` for spacing 



___

Input

To accept more than one input , we can use a for loop along with input function
```python
a, b = [ int(x) for x in input("Enter two numbers: ").split() ]
```
Inputs are divided based on the space

```python
>>> a, b, c = [ int(x) for x in input("Enter three numbers: ").split()]
Enter three numbers: 4 5 6

>>> a * b * c
120

# For accepting string
>>> a, b, c = [ x for x in input("Enter three names: ").split()]
Enter three names: Ram Raj Rocket

>>> print(f"{a} met {b} and went on {c}")
Ram met Raj and went on Rocket
```

```python
>>> a, b, c = [ x for x in input("Enter strings: ").split(',')]
Enter strings: ram, raj, rocket
>>> print(f"You entered {a}  {b}  {c}")
You entered ram   raj   rocket

>>> lst = [ x for x in input("Enter strings: ").split(',')]
Enter strings: ram mohan, raja ram, rocket pack, addded to lst
>>> print(f"You entered : {lst}")
You entered : ['ram mohan', ' raja ram', ' rocket pack', ' addded to list']

```


the `eval()` function takes a string and evaluates the results of the string by taking it as a python expression. `a + b -4`
A list or tuple can be typed into a eval and it understands based on the `[]` or () used in it.


___

Command line arguments

`len(argv)`