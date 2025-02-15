
A decorator is a function that accepts a function as a parameter and returns a function.

A decorator takes the result of a function, modifies the result and returns it.
Thus Decorators are useful to perform some additional processing required by a function.

We should define a function with another function name as parameter.
`def decor(func)`

We should define a function inside the decorator function. This function actually modifies or decorates the values of the passed decorator function.

```python
def decor(func):
	def inner():
		value = func() ## call func and get value
		return value+2
	return inner  # return inner function
```

The last line is returning the inner function which decorated the value.

Once the decorator is created, it can be used for any function to process(decorate) its results. (for understanding the workings of decorator)

```python
def decor(func):
	def inner():
		value = func() ## call func and get value
		return value+2
	return inner  # return inner function

def num():
	return 10

result_func = decor(num)

print( result_func() )
```
`num()` which return 10 is passed to `decor()` function.
the value returned by it is incremented by 2 and the returned `inner()` function is referenced by `result_func` so now it indicates the resultant function.
Calling this function prints the result as 12.

To apply a decorator to any function, we can use the symbol `@` and the decorator name just above the **function definition**.
```
@decor
def num():
	return 10
```

It means the decor function is applied to process or decorate the result of `num()` function.

When it is defined like this, we need not call the decorator function explicitly and pass the function to it.
we can just call `num()` naturally and the associated decorator gets called automatically.

```python
def decor1(func):
	def inner():
		value = func() ## call func and get value
		return value+2
	return inner  # return inner function

def decor2(func):
	def inner():
		value = func()
		return value*2
	return inner


@decor1
@decor2
def num():
	return 10

print( num() )
```
`num` return to `decor2` and `decor2` returns to `decor1`
Without `@` it would have been
```python
result_func = decor1( decor2( num()))
print( result_func() )
```

So the syntax of decorator is 
```
@dec1
@dec2
def func(arg1, arg2, ...):
	pass
```
which is equivalent to 
```
def func(arg1, arg2, ...):
	pass
func = dec1( dec2 (func))
```