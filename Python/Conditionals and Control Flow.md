
```c
>   greter than
>=  greater than or equal to
<   less than
<=  less than or equal to
==  Check if it is equal, comparing on left and right
!=  Not equal to
```


## Control Flow using using if, for and while


### Conditional Execution

Boolean expressions (True  False), it keeps track of certain conditions and provide efficient way to track conditions that are important.
```python
if m%n != 0:     # second statement is executed only if m%n != 0 is True
    (m,n) = (n, m%n)
    
# Alternate Execution
if m%n != 0:
    (m,n) = (n, m%n)
else:
    gcd = n   # else: is optional
```


Numeric value `0`, Empty sequence `""` , `[]` is treated as False
if `m%n` is True if there is reminder, is False if remainder is `0`.

Checking weather a value is in list `"Mushroom" in list`

Checking weather a value is not in list
```python
if user not in banned_users:
	print (f"{user.title()}, you can post a response.")
```

`if` statements
once you understand conditional tests, you can write if statements.
- simplest if has one condition and one action.

`If else` statements
taking one action when condition passes, and a different one in all other cases.

`If elif else` chain
when more than two possible situations need to be considered.  
It is run in order, if any test is executed, python skips the rest
- these are applicable if we are checking for only one condition

`If If If chain`   
to check for multiple checks (all the checks) even if one is already true.


### Multi-way Branching

```python
if x == 1
    y = f1(x)
else:
    if x == 2:
        y = f2(x)
    else:
        if x == 3:
            y = f3(x)
        else:
            y = f4(x)
 # This type of indentation is hard to read while doing a multi check

if x == 1
    y = f1(x)
elif x == 2:
    y = f2(x)
elif x == 3:
    y = f3(x)
else:
    y = f4(x)
```


### Using if statements with lists

Checking for special values  (if else)
Checking that a list is not empty
When name of a list is used in an if statement, python returns true if the list contains atleast 1 item.
```python
request = []
	if request:
		for _ in request:
			print(f"Adding {_}.")
		else:
			print("you want something? ")

# Using multiple lists
# Checking and comparing between two lists

having = [......]     ordered = [..]
    for _ in ordered:
        if _ is having:
            print (f"adding, {_}")
        else:
	        print(f"Sorry, we dont have {_}")
```


## Loops / Repeat the action
```python
# Repeat something a fixed number of times
    for i in [1,2,3,4]:
        y = y*i
        z = z+1
    for i in range(0,n)    # sequece from 0 to n-1
# we can provide a list ask to go through the list


# Finding all factors of a number n
def factors(n):
    flist=[]
    for i in range (1,n+1):
        if n%i == 0:
            flsit = flist + [i]   # flist.append(i)
    return(flist)
```


## Loops based on condition

when not knowing how many number of repetitions are needed
	Executes the body if condition evaluates to True
	After each iteration, checks the condition again
	if condition never changes then it ends up in forever loop
so body must contain a way to progress towards termination by making the condition False
```python
#   Euclid's gcd algorithm
while m%n != 0
    (m,n) = (n, m%n)
return(n)
```


## Altering control flow
```python
if   elif   else  - conditional execution  
for i in range   - repeat a fixed number of times
while           - repeat based on a condition
```


# while loop

"while" allows asking a question to get T or F and runs untill it is T
Indentation is way of making code a part of a thing.
`Crt + C` will cancel program the infinite loop.
```python
# decremented by 1
i=3
while i != 0:
    print("Meow")
    i=i-1

# it can also be incremental by 1
i=0
while i != 3:    # while i<3:
    print("Meow")
    i=i+1        # i += 1
```

While loop - runs till a certain condition is true

Writing clear prompts
To write a prompt for two lines, `+=` can be used, it adds the value to the value already in the variable. can also be used to increase value in a loop.
```python
prompt = "type this message\n"
prompt += "add quit\n:"
message = ""
while message != "quit":
    message = input(prompt)
    print(message)                          

number = 1
while number <= 5:
    print(number)
    number += 1    # number += number   (doubling value)  
```

## Using a Flag to exit loop

If many possible events might occur to stop the program, trying to test all these conditions in one while statement becomes complicated and difficult.
For a program that should run only as long as many conditions are true, you can define one variable that determines whether or not the entire program is active. This variable, called a flag, acts as a signal to the program.

We can write our programs so they run while the flag is set to True and stop running when any of several events sets the value of the flag to False. As a result, our overall while statement needs to check only one condition: whether the flag is currently True.

Then, all our other tests (to see if an event has occurred that should set the flag to False) can be neatly organized in the rest of the program.
```python
prompt = "\nType to have it repeated"
prompt += "\n: "
active = True

while active:               # active is True unless it is changed by if
    message = input(prompt)
    if message == "quit":
        active=False # when something happens that turns flag to False, loop quits
    else:
        print(message)              

# Using break to Exit loop
prompt = "\nEnter the city you have visited:"
prompt += "\nuse quit to exit.  "

while True:                  # setting condition to true
    city = input(prompt)
    if city == "quit":
        break                # using if and break to exit the loop
    else:
        print (f"\n{city.title()} is lovely")
```

Using continue in a loop
Rather than breaking out of the entirely, continiue can be used to return to the beginning of the loop.
To skip even numbers but print all odd numbers while running a sequence
```python
number= 0

while number <10:
    number += 1
    if number%2 == 0:
        continue            # return to beginning, skips else, doesnt break
    else:
        print(number)
```

Using while loop with Dict and List
Do not modify a list inside a for loop, use while loop to modify a list as u work through it.

Moving items from one list to another
```python
unconfirmed_users = ['alice', 'brian', 'candace']
confirmed_users = []

while unconfirmed_users: # stays True till there is value, empty list is False
    user = unconfirmed_users.pop()
    print (f"Verifying User: {user.title()}")
    confirmed_users.append(user)
print (f"\nThe following users have been verified:")

for _ in confirmed_users:
    print(f"{_.title()}")          
```

Removing all specific values from a list.
`remove()` gets one instance of a value, if there are many more then it needs to be looped.
```python
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
print(pets)

while "cat" in pets:
    pets.remove("cat")
print(pets)                        
```

Filling a Dictionary with user input
```python
responses = {}
polling = True

while polling:
    name = input(f"\nWhat's your name: ")
    response = input(f"What mountain you want to climb someday?: ")
    responses[name] = response   # name is key, response is value, added to {}
    
    repeat = input("\nWould you like another to take this poll?( y/n): ")
    if repeat == "n":
        polling = False  
        # could have used break also but flag seems more practical in other programs

print("\n-- Poll Results --")
for name, response in responses.items():
    print (f"{name.title()} wants to climb {response.title()}.")
```

## for loop

for loop - takes a collection of items and executes a code block once for each item in the list.
"for" allows you to iterate over a list of items.
```python
for i in [0, 1, 2]:
    print ("meow")

for i in range(3):         
    print("meow")
```
"in" is just a new for stating value in the list,  "i" is initialize with 0 first, then 1 and then 2.
end of numbers in the list it will stop print.
`range()` function will hand out whatever number of values it is specified

```python
# only a python feature
print ("meow" * 3)              # will be meowmeowmeow
print ("meow\n" * 3)            # using an escap sequence like "\n" gives new lines
                                # but has an extra line
print ("meow\n" *3, end="")     # removing the default "\n" parameter of print function
                                # kind of difficult to read
```

```python
def main():
    number = get_number()
    meow(number)
  
def get_number():
    while True:
        n = int(input("whats n? "))
        if n>0:
            break   # it can just be "return n" insteaf of "break" within the loop
    return n        
# even with break, there has to be a "return n" outside the loop but within the function.

def meow(n):   
    for _ in range(n):       
        print("meow")
        
main()

# call "main", which calls "get_number" to get a positive input only and pass it to "meow"
# "main" calls "meow" which has the "int" to run it that many times
# "meow" runs for "_" number to the "int range" and stops
```

## Using while loop to simulate for loop

```python
for n in range (i, j):
    statement
n=i
while n<j:
    statement
    n = n+1


for n in l:
    statement
i = 0
while i < len(l):
    n = l[i]
    statement
    i = i+1
```

# CS50 Conditionals
```python
# Conditions which allow to take forks in your own road

# Boolian expression, an Yes or No

x = int(input( "what is x? "))
y = int(input( "what is y? "))
if x<y:
    print("x is less than y")
if x>y:
    print("x is greater than y")
if x==y:
    print("x is equal to y")

# whether the firsr one is true or false, it will execute all the lines asking three questions

if x<y:
    print("x is less than y")
elif x>y:
    print("x is greater than y")
elif x==y:
    print("x is equal to y")
    

# elif which is else if is done to avoid unnecessary execution repetetion
# if x < y isnt true, else if is executed, otherwise stopped

if x<y:
    print("x is less than y")
elif x>y:
    print("x is greater than y")
else:
    print("x is equal to y")

# else can be used in the last one
# else isnt condition, just saying execution if nothing was True


if x > y or x < y:      # "or" condition is used to reduce two to one line
    print("x is not equal to y")
else: 
	print("x is equal to y")        


if x != y:        # we can just use != or ==, insted of using x>y or x<y
    print("x is not equal to y")
else: 
	print("x is equal to y")
```

```python
score = int(input("Score: "))

if score >=90:
    print("Grade: A")
elif score >=80:
    print("Grade: B")
elif score >=70:
    print("Grade: C")
else:
    print("Grade: F")

# when "if" is used in place of "elif", it will output everything even if first one was true
```

```python CS50
#Parity,  to see if given number is even or odd

if x % 2 == 0:                
    print("x is even")
else:
    print("x is odd")

# "%" is dividing x by the number and getting the reminder, even number/2 is zero
```

```python CS50
# the forth data type is bool for boolian which returns True or False (with capital T and F)

def main():
    x=int(input("what is x? "))
    if is_even(x):         # is_even called and value of x is passed
        print("Even")      # is_even() is defined to return a boolian value of T or F
    else:    # it is not nesessary that it has to be a number, T or F is enough conditionl to print
        print("Odd")

def is_even(n):
    if n % 2 == 0:       
        return True
    else:
        return False
main()
```

```python
# functions like .strip() .capitalize() .title() is part of str,
# if our function returns a str, then these can be used

def main():
    x=int(input("what is x? "))
    if is_even(x):          
        print("Even")            
    else:                  
        print("Odd")

def is_even(n):
    return n % 2 == 0    # n%2==0 by itself a boolian expression which returns T or F
main()                   # So there actually no need of returning extra T or F as in "True if n % 2 == 0 else False"
```

```python 
name = ("what is your name? ")
if name == "Harry" or name == "Hermione" or name == "Ron":
    print("Gryffindor")                                    
elif name == "Draco":
    print("Slytherin")
else:
    print("who?")

# if isn't a function so doesnt need (), maybe it can have
# or is used to reduce 3 into 1
  
  
# "match" (similar to switch in other languages)
# using "match" and its cases to compare
name = input("what is your name? ")
match name:
    case "Harry":
        print("Gryffindor")
    case "Hermione":
        print("Gryffindor")
    case "Draco":
        print("Slytherine")
    case _:                        
        print("Who?")
# "_" underscore is used to cover any undefined cases

  

# "|" a vertical bar is used kind of "or"
name = input("what is your name? ")
match name:
    case "Harry" | "Hermione" | "Ron":      
        print("Gryffindor")
    case "Draco":
        print("Slytherine")
    case _:                          
        print("Who?")
```

