```python

Class Person:

	def __init__(self, fname, lname): # always returns None
		self.fname = fname    # these can be different but by convention same
		self.lname = lname

	def __str__(self):
		return f"person: {self.fname} {self.lname}"

	def say_hi(self):
		print (f"{self.fname} says hi")


# Creating instances
person1 = Person("John", "Doe") 
person2 = Person("Walter", "jack")
```

```c
What i understand is,
the constructor method constructs the "object"/"instance" from the template of class "Person".
Now the "Person1" and "Person2" are uniqie and sepearate objects with the values within them (that is the instance variables)

So "person1" has 
person1.fname = "John"
person1.fname = "Doe"
and the rest of the def and "methods"/functions contained in it.... 

so it has all the required data and functions to anything related to a person, allowing each method to be called by referring to whatever is in 'self' place along with 'method' name. 
'method' already have 'self' so it can utilize the 'instance variables'


i can just call
	print(person1.fname) and it will return "John"
	person1.say_hi()

it was not passed to any function but has all the data "init", all the "methods"/function calls also "person1.say_hi" will return some answer but no function was called as the function and the required data is present within each "object"

So an object is like a "Container" independent.
```

# Class variables and Instance variables
```c
Class variables: if i assign a value inside the class, then every instance will have the same value. These do not need "self" as they are availbale to all

Instance variable: The value passed on through the init while creating the instance will be uniqe to every objects.
```


# Inheritance
```python
class Animal:

	def __init__(name, age, no_legs):
		self.name = name
		self.age = age
		self.legs = no_legs

	def __str__(self):
		return f"name: {self.name}"

	def speak(self):
		print (f"{self.name} is not able to speak")


class Dog(Animal):

	def __init__(name, age, no_legs, breed):
		super().__init__(name, age, no_legs)   # no self again
		self.breed = breed
		self.type = "Dog"

	def __str__(self):
		return f"name: {self.name}, breed: {self.breed} {self.type}"	
	
	def speak(self):
		print (f"The {self.name} can bark" )	
```

```c
The class animal is given the characteristics of an animal, and initialized.

class Dog can inherit the methods of Animal as they will be same.
So passing class"Animal" as argument to indicate it is the super class.
using "super().__init__(arguments)" to initialize the common arguments and updating the extra ones separately.

Any additional "instance variables" can be added.

If there are any "methods" which are simlar, the one in the "super() class" will be overridden by the one in the other class.

This is polimorphism??
Inherit from multiple Classes??
```


# Decorators
```c
@property

does the work of assigning a variable in the "__init__" method.

def __init__(...):
	self.fullname = fname + lname

@property
def fullname(self):
	return f"{self.fname} {self.lname}"


both do the same thing

print(person1.fname)
print(person1.fullname)      will return same for both
# no need of () because fullname is a property, which is similar to an instance variable.
```

```c
@class

this decorator creates another class from existing oject??
It takes class as its first argument, not self because it creates a class

I cant see the use of this in lower necessary level
```

Getters and Setters
```c
Using a "method" to just return the value acts as a getter.
	@property
	def salary(self):
		return self.__salary
# getter returns the salary


Setter is bit more, without allowing for decrement of value but just increment.
using the new feature of "match :  case"
which not only compares but also assigns value to variable in process(a two in one process compared to if elif)

	@salary.setter
	def salary(self, amt):
		if self.role == Role.ASSOCIATE and amt <15:
			print("Error! Associate cannot have salary less than 15/hr)
	# setter sets salary after validation
```


## @final - a decorator to designate a class as final so it cannot be inherited by any other class.

## @staticmethod - 