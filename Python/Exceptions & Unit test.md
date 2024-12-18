Exceptions are special objects python creates to manage errors that arises while the program is running.

Predictable errors - exception
Contingency plan - Exception handling

Recovering Gracefully from errors
	Try to anticipate errors
	 Provide a contingency plan
	 Exception handling
Un-handled exception aborts execution 

## Types of Errors
```python
# most common errors
# code wont run
SyntaxError: invalid syntax     # not a valid python code, not much error handling

# RuntimeErrors: Errors when code is running
NameError: name 'x' is not defined # name used before it is defined

ValueError: invalid literal error   for int() with base 10: 'cat'

ZeroDivisionError: division by zero   # trying to divide by zero

IndexError: list assignment index out of range  # invalid list index

KeyError:  # dictionary key doesnt exist
```

## Handling exceptions
```python
# to make sure code runs without crashing
try:
    x = int( input ("what is x? "))
    print (f"x is {x}")
except ValueError:
    print ("x is not an integer")


try:
	...   # code where error may occur
	...
except IndexError:
	...   # Handling Index Error
except (NameError, KeyError):   # Handling multiple errors at a time
	...   # Handling multiple errors
except:   # with no specific error to catch any other error generally
	...
else:
	...   # If no error, execute if code ran without any error 
```

## Using exceptions "positively"
```python
# Traditional approach
b = {}
if b in scores.keys():    # check if a key exists in dictionary 
	scores[b].append(s)   # then append
else:
	scores[b] = [s]       # if it doesnt, create the key and add value


# Using exceptions  (a way of programming)
try:
	score[b].append(s)
except KeyError:        # if the key didnt exist it shows KeyError
	score[b] = [s]     # handle it by adding new value
```

## Flow of control

If a function calls function in a nested fashion and error occurs at the last function.
The error gets passed back to calling functions without aborting,
If it gets handled by try, except then it wont abort.

Even if the final calling function doesn't handle it, then program abort

```python
# instead of quitting the program because the input wasnt right
# using "loops" to prompt again till value is right

while True:
    try:
        x = int ( input ("what is x? "))
    except ValueError:
        print("x is not an integer")
    else:                   # "else" is not associated with "except" but with "try"
        break               #  exception happens then it loops Except is true?
    # No "exeption" then skips "except" and executes "else" and breaks when x is int()
print (f"x is {x}")                    # and prints with the x
                 # if print was below "else" it wouldnt break out of the loop
```

```python
while True:
    try:
        x = int (input( "what is x? "))
        break               # if x gets a value, then it breaks, so simple
    except ValueError:      # exception, then print and loop to input
        print("x is not an integer")
print(f"x is {x}")
```

"return x" is used instead of "break" as return does the same but also returns the value also
defining a function get_int() of our own which gets int.
```python
def get_int():
    while True:
        try:
            x = int( input( "what is x? "))
            return x
        except ValueError:
            print("x is not an integer")
get_int(x)
print(f"x is {x}")
```

```python
def main():
    get_int()      
    print(f"x is {x}")

def get_int():
    while True:
        try:
            x = int( input( "what is x? "))
            return x
        except ValueError:
            print("x is not an integer")
main()
```

Correcting value passing of x
```python
def main():              
    x = get_int()                
    print(f"x is {x}")
  
def get_int():
    while True:
        try:
            x = int( input( "what is x? "))     # return int(input("what is x? "))
            return x                  # this line just directly returns without having to initialise a variable x
        except ValueError:             # just might make it difficult to read
            print("x is not an integer")
main()  
```
### Pass
```python
# instead of giving user error messgage,and prompting them to enter x
# reprompting for input x without error can be done with pass
# silently ignoring it like pass

def main():              
    x = get_int()                
    print(f"x is {x}")

def get_int():
    while True:
        try:
            x = int( input( "what is x? "))
            return x                      
        except ValueError:              # except catches the value error
            pass                        # pass is to just ignores it
main()
```

### Reusable Function
```python
# by not specifying what a "calee" the function thats being called to have a prompt
# but letting the "caller" function thats calling to decide the prompt
# so caller should "pass" what is wants to be prompted to "calee"
# working
# Caller passes the statement, calee recieves the argument and uses it to return the value

def main():              
    x = get_int("what is x? ") #main is calling "get_int" giving it argument it wants   
    print(f"x is {x}")                # x is whatever "get_int" returns

def get_int(prompt):                    # "get_int" gets the argument
    while True:
        try:
            x = int( input(prompt))     # gets the input and passes to x
            return x                      # x is passed to main()
        except ValueError:          
            pass                      
main()
```



# Unit test
```python CS50
writing code to test the code we have written

assert # is keyword which asserts something is true
# if its not true, there will be an "AssertionError"

from calculator import square    # import square from calculator, this doesnt work??
def main():
    test_square()

def test_square():
    assert square(2) == 4   # the square was supposed to be imported from another function
    assert square(3) == 9  # insted of  if square(2) != 4:
                             #        print("2 squared was not 4") better to use assert
if __name__ == "__main__":
    main()
```
      
```python
from calculator import square

def main():
    test_square()

def test_square():
    try:
        assert square(2) == 4
    except AssertionError:
        print("2 squared was not 4")
    try:    
        assert square(3) == 9
    except AssertionError:
        print("3 squared was not 9")

if __name__ == "__main__":
    main()

# there is more code than using "if", but "assert" is used and error is handled
# more code to test two lines of code
```

```python
"pytest" is the tool which can be used to test the code
# pytest will handel the try, except and printing which are standard procedure
# pytest can be installed by "pip install pytest"
# docs.pytest.org
# there are more built into python

from calculator import square

def test_square():
    assert square(2)==4
    assert square(-2)==4
    assert square(3)==9
    assert square(0)==0

# the program is run in command line as
# "pytest filename.py"

# breaking the logic into various fuctions allows for easy testing and debugging, with logic all over the program itll be difficult to find or fix.
# each function should have well defined input and well defined output


# the test square can be divided into few more categories like possitive and negative
# testing one more with string

def main():
    name = input (" whats your name? ")
    hello(name)

def hello(to="world"):
    print("hello,", to)

if __name__ == "__main__":
    main()

# testing program
from hello import hello

def test_hello():
    hello("David") == "hello, David"

# this will fail because testing program is testing the output handed by the hello program but hello is not returning anything, its effects are just "side effcts", printing on the screen, nothing is returned so nothing to test
```

It's best practice to reduce "side effects"
```python
print( " hello,", to) # so insted of
return f"hello, {to}"   # then print in main()
 
```