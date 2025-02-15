
functions are a group of statements that perform a specific task, is called by its name.

a function written inside a class becomes a method and is called by either
`objectname.methodname()`
`Classname.methodname()`

____

functions are firs class objects, using functions as perfect objects

Since functions are objects, we can pass functions to another function similar to passing values and also possible to return a function.
functionsa assigned to variables
function within another function'



___

returning multiple values from a function

return a, b , c

x, y, x = function()

___

Pass by value and reference is not applicable to python, since everything is an object, everything is passed by object reference 
so values of immutable values like strings, int, float cannot be changed inside a function and also be changed outside.

mutable objects like list and dictionaries can be passed and be changed, no new object will be created but the vales in the old one will be updated.

Object created inside a function will not be available outside


___

Formal arguments
are parameters that are there when a function is defined to recieve values from outside.
When function is called, the data or values passed to the function are called actual arguments.

Positional arguments - passing in right order
key word argumnts - assigning to variables and passing in any order. Identifying the parameters by their names.
Default 

fargs - formal argument
Variable length arguments - can accept any number of arguments.
`*args` stores the variable in tuple

`**kwargs`
a keyword variable length argument is an argument that can accept any number of values provided in the format of keys and values.
If we want to use key word variable length argument we can declare ti with `**` before the argument as `**kwargs`
`def display(farg, **kwargs)`
`display(f, rno =10 )`
	now `rno` is key and its values `10` is stored in the dictionary that is referenced by kwargs.

```python
def display(farg, **kwargs):
    print('Formal argument: ', farg)
    for x, y in kwargs.items():
        print(f"key = {x}, value = {y}")

display(5, rho=10, name="Uname", cd="UNNCD")
```

```
Formal argument:  5
key = rho, value = 10
key = name, value = Uname
key = cd, value = UNNCD
```

____

Global Keyword to make a a local inside a function into a global variable (it is a way to apply the changes made in a function to be refleced on the previously defined  outer variable.) 
To use the global variable inside the function 


___

Passing a group of elements to a Function

By putting them in a list and passing the list and processing it.
`lst = [ int(x) for x in input().split() ]`

