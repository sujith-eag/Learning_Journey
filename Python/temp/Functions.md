
A function is a set of statements which performs a task. They are called with different arguments. It is a bundled computations which can be called repeatedly.
```python
def f(a,b,c):
    statement_1
    statement_2
    ..
    return(v)
```
Function name, arguments/parameters, body is indented,  `return()` statement exits and returns a value.

## Passing values to function

It is done similar to assigning values to a name 
```python
def(x, n):
def(3, 5):
# then implicitly the value gets assigned as implicit assigment statement
x = 3
n = 5

# but it can be assigned out of order by spevifying the name
def power(x,n):

call (power(n=5,x=4) )
```

Immutable value will not be affected at calling point, Mutable values will be affected.
```python
def update (l,i,v):
    if i>=0 and i<len(l):  # checking if i lies b/w o and len(l)
        l[i] = v
        return(True)
    else:
        v = v+1
        return(False)

# l is a list, i is the possition, v is the value that has to be replaced
ns = [3,11,12]
z = 8

update(ns,2,z)   # in ns, 3rd object, changed to z ie 8
update(ns,4,z)   # in ns, 5th object change to z, but there is no 5th place
```
so v which in 8 gets incremented to 9, but the actual value of Z will not change as v is immutable.
There isn't change if the value is immutable but mutable values get changed (didn't understand whats this about)

## Default Arguments of Function

```python
int() # converts string to integer

int(s,b) string is s, base is b
# the second value automatically considers as base 10 when parameter is omited
int(s,b=10)
so
int("76") = 76
int("A5") is error

# assigning base 16
int("A5", 16) = 165   
```

The default value of a function must be available at definition time
```python
def Quicksort(A, l=0, r=len(A)):
    # this will not work as default value as r is dependent on A
    # the values should be defined before run time

def fan(a, b, c=14, d=22):   # here c and d has default values
```
f(13,12) will be f(13,12,14,22),  f(13,12,16) will be f(13,12,16,22), the values are assigned as per the position so order is important.

## Function Definition

`def` associates a "body" with a "name"
Name can be reassigned and even different body can be assigned using conditionals
```python
if condition:
    def f(a,b,c):
    ...
else:
    def f(a,b,c):
    . . . .
```

## Function to a different name

```python
def f(a,b,c):
    . . .

g = f       # g is now another name for f
# this is useful to assign a function as argument to another function

def apply(f,x,n):
    res = x
    for i in range(n):
        res = f(res)
    return(res)

def square(x):
    return(x*x)

apply(square, 5, 2)
    # this will be square(square(5))    625
```
Here function square is passed as f = square to another function

## Customizing function

```
def sortfunction(l, cmpfn = defaultcmpfn)

it can be sorted by number of elements or based on alphabets order
```

_____

## Scope of Function
#21aug24

Scope of names - names within a function are disjoint from the names outside of the function.
By default, in python, scope is local to functions, but only if we update the name inside the function. If value is not found in `f()`, python looks at enclosing function for global x.
```python
def f():              def f():
	y = x                 y = x
	print(y)              print(y)
                          x = 22
x = 7                
f()    runs fine      x = 7   error, x called before defining
	                  f()
```

In second case function sees the x inside, doesnt check the external definition. 
Here x is updated inside `f()` hence it became a local name.
in first case, there is no x inside the function so it checks outside.
this applies only to immutable values.

Global variables
	list, dict are global and need no be passed around as they are mutable values. Global names that point to mutable values can be updated within a function.
```python
def f():
	y = x[0]
	print(y)
    x[0] = 22
    
x = [7]        # x is a list now
f()            # runs and returns 7 and x also gets updated
```

Global immutable values (global integer)
	as for counting the number of times a function is called.
	declare the name to be global
```python
def f():
	global x   # stating all x are same values
	y = x
	print(y)
    x = 22
    
x = 7        # x is a list now
f()       # runs and returns 7 and x also gets updated
print(x)  # gives 22
```

## Nested function

function within a function called "helper" functions
```python
def f():
	def g(a):
		return(a+1)
	def h(b):
		return(2*b)

	gobal x
	y = g(x) + h(x)
	print(y)
	x = 22

x = 7
f()
```
Here `g()` and `h()` are local to `f()`, they are not available or visible to outside calling. it is kind od hidden for outside.
similarly, if x isn't available, it looks outside. if mutable can update globally

## CS50 on Functions

Looking into creating our own functions to use it most of the places by calling on it.
`def` is define which allows defining your own function, by typing def naming the function, parenthesis`()`, and `:` the defining begins.
Whatever gets indented below it is treated as part of the function.
```python CS50
def hello(to):
    print("hello,", to)
name = input ("whats your name? ")

hello(name)
```

functions have`()`, optional are `[]`, to create new arguments `,` can be used.
methods have `=` and assigning values is also `=`,  `""` and `''` are interchangeable.
The parameter for `hello()` is assigned as (to)

Giving default value to the function like script had `sep=' '` and `end='\n'`
If no value is provided default can run, if defined it gets replaced.
```python
def hello(to="world"):  # defining hello, with parameter to, and default value world,:
    print("hello,", to )   # prints srting hello, with another variable to
hello()                 # calling hello()  prints hello world, asks input
name = input("whats your name? ")    
hello(name)  # calling again with hello as argument, replaces value of to and gives name
```

In this it is asking for name and calling name function.
main is defined, hello is defined,then main() function is called.
```python
def main():
    name=input("whats your name? ")    
    hello(name)   # input is taken, hello is called and input is passed to hello()  

def hello(to = "world"):    # input becomes value of variable "to"
    print("hello,", to)     # prints hello and input
main()
```

Issue of scope of variable
```python
def main():
    name=input("whats your name? ")    
    hello()  # hello is called without argument, ie not passing the input value    

def hello():               # hello is defined without argument
    print("hello,", name)  # name is directly called from the main function but name only exists in main        # so there will be an error  
main()
```

Issue of "Scope" which refers to a variable only existing in the context it was defined in name was defined in `main()` so it cannot be used directly in `hello()`.
When the value is handed to `hello()` within the `main()`, it can be used.
Its for each function to name its own variable so the "name" variable in main can be passed to "hello" which becomes "to"
"return" a key word can be used to return the value back to another function.
```python
def main():
    x = int(input("whats x? "))
    print( "value of x squared is,", square(x))

def square(n):
    return n*n          # the return function passes the value back to main function
    return n**2         # ** is raising power
    return pow(n, 2)    # pow is for raising power
main()
```



# Python Crash Course
## Chapter 8 - Functions

Functions, which are named blocks of code designed to do one specific job.
When you want to perform a particular task that you've defined in a function, you call the function responsible for it.

If you need to perform that task multiple times throughout your program, you don't need to type all the code for the same task again and again;

Defining a function
'def' for defining a function, naming and passing parameter.
`""" """` is doc string which will be used to make documentation.    
What's indented is the body of the function.
function call is used to call the function and passing argument.

```python
# Passing informatin to a function

def greet(username):      # by adding value to (), allows it to accept value
    print(f"Hello, {username.title()}")
greet("jess")             # value gets passed to function  
```


Arguments and Parameters
The variable in function is the parameter, the value passed to function is argument

Passing Arguments
Positional arguments - which needs to be in the same order as the parameters

keyword arguments - consisting of a variable name and a value; and list and dict of values

### Positional arguments

```python
def dis_pet(animal, name):
    print (f"\nI have a {animal.title()}")
    print(f"It's name is {name.title()}")
dis_pet("hammster", "harry")
dis_pet("dog", "Jack")          # multiple function calls    
```

### Keyword Arguments
It is the key word arguments passed to the function, so there is no confusion or ordering the value.

```python  
def dis_pet(animal, name):
    print (f"\nI have a {animal.title()}")
    print(f"It's name is {name.title()}")

dis_pet(animal = "hammster", name = "harry")
dis_pet("dog", "Jack")              
```
## Default values

When writing a function, you can define a default value for each parameter.
If an argument for a parameter is provided in the function call, Python uses the argument value.
If not, it uses the parameter's default value.

So when you define a default value for a parameter, you can exclude the corresponding argument you'd usually write in the function call.

Using default values can simplify your function calls and clarify the ways your functions are typically used.

Equivalent function calls
Because positional arguments, keyword arguments, and default values can all be used together, you'll often have several equivalent ways to call a function.


```python
def dis_pet(animal, name = "will"):
    print (f"\nI have a {animal.title()}")
    print(f"It's name is {name.title()}")

dis_pet(name = "harry", animal = "hammster")
dis_pet("dog", "Jack")
dis_pet("cat")              # the name will default to will unless specified
```

When you use default values, any parameter with a default value needs to be listed after all the parameters that don't have default values. This allows Python to continue interpreting positional arguments correctly.


## Return Values

The value the function returns is called a return value
The return statement takes the value from within the function and returns it to the line that called the funtion.
```python
# Returning a simple value
def format_name(first, last):
    full_name= f"{first.title()} {last.title()}"
    return full_name               #Just return doesnt work
  
print(format_name("michal", "jackson")) 
# person = format_name("michal", "jackson")
# print(person)
```
## Optional arguments

Making an Argument optional by giving a default value of "" makes an argument optional
```python
def get_formatted_name(first_name, last_name, middle_name=''):
    if middle_name:# python interprets non empty strings as true, empty as false
        full_name = f"{first_name} {middle_name} {last_name}"
    else:
        full_name = f"{first_name} {last_name}"
    return full_name.title()
    
musician = get_formatted_name('jimi', 'hendrix')
print(musician)
musician = get_formatted_name('john', 'hooker', 'lee')
print(musician)                                                    
```
## Returning a Dictionary
```python
def build_person(first_n, last_n):
    person = {"first" : first_n, "last": last_n}
    return person          # i cant put .title() on dict
  
name = build_person("jimi", "hendix")
print(name)
```

```python

def build_person(first_n, last_n, age = None):
    person = {"first" : first_n, "last": last_n}
    if age:
        person["age"] = age  
    return person

name = build_person("jimi", "hendix", "27")
print(name)
```
The optional parameter "age" has special value None as place holder,  In conditional tests, non evaluates to False.


## Using function with a while loop

```python
def get_formatted_name(first_name, last_name):
    full_name = f"{first_name} {last_name}"
    return full_name.title()

while True:
    print("\nPlease tell me your name: ")
    print("(enter 'q' at any time to exit)")

    f_name = input("First Name: ")
    if f_name == "q":
        break

    l_name = input ("Last Name: ")
    if l_name == "q":
        break

    name = get_formatted_name(f_name, l_name)
    print(f"\n{name.title()}")                  
```

## Passing a List
```python
def greething(names):
    for name in names:
        print (f"Hello,{name.title()}.")

Username = ['hannah', 'ty', 'margot']
greething(Username)                    


# without defining a function
unprinted_designs = ['phone case', 'robot pendant', 'dodecahedron']
completed_models = []

while unprinted_designs:
    one = unprinted_designs.pop()
    print(f"The following models are done: {one}")
    completed_models.append(one)

print(f"\nThese have been printed")
for each in completed_models:
    print(each)

  
# With functions
def making_print(tobe,notyet):
    while unprinted_designs:
        one = unprinted_designs.pop()
        print(f"The following models are done: {one}")
        completed_models.append(one)

def last_check(notyet):
    print(f"\nThese have been printed")
    for each in completed_models:
        print(each)

unprinted_designs = ['phone case', 'robot pendant', 'dodecahedron']
completed_models = []

making_print(unprinted_designs, completed_models)
last_check(completed_models)                                    
```

## Passing copy of a list - to prevent a Function from Modifying a List

copy can be sent by  `Name_of_Function(list_name[:])`
        ex-   `print_models(unprinted_designs[:], completed models)`

The slice notation `[:]` makes a copy of the list to send to the function. now the function will recieve a copy.
Its more efficient to work with the existing function than to make a new copy.  


## Passing an arbitrary number of Arguments

When you dont know ahead of time how many arguments a function needs to accept, python allows function to collect an arbitrary no of arguments, from the calling statement.   by using * in parameters, it accespts as many as it is given.


```python
def make_pizza(*toppings):    # the asterisk * in ffront
    print("\nMake Pizza with the following toppings:")
    for topping in toppings:
        print(f"-{topping}")

make_pizza('pepperoni')
make_pizza('mushroom', 'pepper', 'extra cheese')  
```

## Making Positional and Arbitrary arguments
```python
While using both, arbitrary must be in the end, python matches with first and passes rest to the end

def make_pizza(size, *topppings):
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in topppings:
        print(f"-{topping}")

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushroom', 'green pepper', 'cheese')
```

## Using Arbitrary keyword Arguments:
```python
Sometimes you'll want to accept an arbitrary number of arguments, but you won't know ahead of time, what kind of information will be passed to the function.
In this case, you can write functions that accept as many key-value pairs as the calling statement provides.
  

def build_profile(first, last, **user_info):        
#**kwargs, used to collect non-specific keyword arguments
    user_info['first_name'] = first    # Being placed into dictionary with keys
    user_info['last_name'] = last
    return user_info

user_profile = build_profile('albert', 'einstein', location ='princeton', field = 'physics')

print(user_profile)

# Output : {'location': 'princeton', 'field': 'physics', 'first_name': 'albert', 'last_name': 'einstein'}
```
  
## Storing functions in modules
```
With proper descriptive names, functions can be stored in a seperate file called "module" and then "importing" that module into program.

Storing your functions in a separate file allows you to hide the details of your program's code and focus on its higher-level logic.

It also allows you to reuse functions in many different programs. When you store your functions in separate files,

you can share those files with other programmers without having to share the entire program.
```

## Importing an Entire Module, all the functions in a file
```python
A module is a file ending with .py that contains code you want to import

#pizza.py       - Summarize the pizza we are about to make.

def make_pizza(size, *toppings):
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in toppings:
        print(f"- {topping}")

# making_pizzas.py

import pizza
pizza.make_pizza(16, 'pepperoni')
pizza.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
# (name of file).(name_of_function)(parameters)
```

## importing specific functions
```
# from module_name import function_name
# from module_name import function_0, function_1, function_2
# the the module can be directli called without file name - make_pizza()
# Using "as" to give a Functiona an Alias

If the name of a function you're importing might conflict with an existing name in your program, or if the function name is long, you can use a short, unique alias —an alternate name similar to a nickname for the function.

You'll give the function this special nickname when you import the function.

Here we give the function make_pizza() an alias, mp(), by importing make_pizza as mp.

The as keyword renames a function using the alias you provide:
```

```python
from pizza import make_pizza as mp
mp(16, 'pepperoni')
mp(12, 'mushrooms', 'green peppers', 'extra cheese')
  
# The general syntax for providing an alias is:  
from module_name import function_name as fn

  
# Using "as" to give module an Alias -
import module_name as mn
import pizza as p

  
# Importing all Functions in a module
# You can tell Python to import every function in a module by using the asterisk (*) operator:

from pizza import *
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')

# Because every function is imported, you can call each function by name without using the dot notation. However, it's best not to use this approach when you're working with larger modules that you didn't write.
```

