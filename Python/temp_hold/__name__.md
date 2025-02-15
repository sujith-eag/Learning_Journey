when a program is executed in python, there is a special variable internally creaed by the name of `__name__`.
this variable stores inforamation regarding whether the program is executed as an individual program or as a module.

When the program is executed directly, the interpreter stores the value `__main__` into this variable.

When a program is imported as a module into another program, the interpreter stores the module name into this variable.

So by observing the value in variable `__name__` we can understand how the program is executed.

if `__name__` variable does not contain value `__main__`, it represents that this code is run as a module from another external program.

```python
if __name__ == '__main__':
	main()
```

Is used to make sure the imported programs do not execute if they are not called directly.


