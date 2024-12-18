# Some more clarity on this






## Classes / Abstract Data Type (Python Crash Course)

Class is user defined data type. Classes are used to construct new data types other than the standard ones using Class as a template.

The behaviour of this data type is defined through an interface.
Stores some information and can also have designated function to manipulate the information. Like a black box with few function accesible. 

stack: is last-in, first-out, it has operations `push( )` and `pop( )`.
	`(s.push(v)).pop() == v`   what gets put in comes out next.
	
Queue: `addq()` and `removeq()`
	`((q.addq(u)).addq(v)).removeq() == u`    if 2 are added, first one comes out 

Heap: `insert()` and `delete_max()`

Here a List is defined as a Stack, and heap which is a publicaly available function but the implementation should be private. implimentation can be optimized without affecting functionality and it should not be obvious.
Separate the (private) implementation from the (public) specification.

So no manipulations like in between insertion and extraction should not be done even if it is made of list like append, extend.

### OOP

In object oriented programming you write classes that represent real-world things and situations, and you create objects based on these classes.
Class is a template, then the copies of these templates are objects as many copies/instances of objects can be made.
When you write class, you define the general behavior that a whole category of objects can have.
When you create individual objects from the class, each object is automatically equipped with the general behavior; you can then give each object whatever unique traits you desire.
Making an object from a class is called instantiation, and you work with instances of a class.

By convention, capitalized names refer to classes in Python.
There are no parentheses in the class definition because we're creating this class from scratch.


The `__init__()` method is the constructor function thats part of a class is a method that constructs new instances based on argument.

The `__init__()` method is a special method that Python runs automatically whenever we create a new instance based on any Class.

Everything related to functions applies to methods as well; the only practical difference will be in how class methods are called.

We define the `__init__()` method to have three parameters: self, name and age.
The self parameter is required in the method definition, and it must come first, before the other parameters.
It must be included in the definition because when Python calls this method later (to create an instance of Dog), the method call will automatically pass the self argument.
  
Every method call associated with an instance automatically passes self.
self is a reference to the instance itself; as each object is different, and they have a unique copy of the Class functions. While calling, each object is called specifically with its name, so self is needed to apply whatever the function is to itself.

It gives the individual instance access to the attributes and methods in the class.
When we make an instance of Dog, Python will call the `__init__()` method from the Dog class. We'll pass `Dog()` a name and an age as arguments;

'self' is passed automatically, so we don't need to pass it.
Whenever we want to make an instance from the Dog class, we'll provide values for only the last two parameters.

  
The variables defined in the body of the `__init__()` method will also have the prefix self.
Any variable prefixed with self is available to every method in the class, and we'll also be able to access these variables through any instance created from the class.

The line `self.name = name` takes the value associated with the parameter 'name' and assigns it to the 'variable name', which is then attached to the instance being created. Variables that are accessible through instances like this are called 'attributes'.

The Dog class has two other methods defined: `sit()` and `roll_over()`.
Because these methods don't need additional information to run, we just define them to have one parameter, self.

The instances we create later will have access to these methods. In other words, they'll be able to sit and roll over.

Making an instance from a class.
Think of a class as a set of instructions for how to make an instance.
The Dog class is a set of instructions that tells Python how to make individual instances representing specific dogs.

```python
# Creating and using a Class
    # Creating the Dog Class
class Dog:
    def __init__(self, name, age):  # Initialize name and age attributes.
        self.name = name
        self.age = age
  
    def sit(self):        # Simulate a dog sitting in response to a command.
        print(f"{self.name} is now sitting.")

    def roll_over(self):       # Simulate rolling over in response to a command.
        print(f"{self.name} rolled over!")

my_dog = Dog('Willie', 6)     # a dog object is created by calling class
your_dog = Dog('Lucy', 3)

print(f"My dog's name is {my_dog.name}.")
print(f"My dog is {my_dog.age} years old.")
my_dog.sit()

print(f"\nYour dog's name is {your_dog.name}.")
print(f"Your dog is {your_dog.age} years old.")
your_dog.sit()        
```

****

```python
class Restaurant:
    def __init__(self, restaurant_name, cuisine_type):
        self.restaurant_name = restaurant_name
        self.cuisine_type = cuisine_type

    def describe_restaurant(self):
        print(f"{self.restaurant_name} has {self.cuisine_type} as special cuisine")

    def open_restaurant(self):
        print(f"\nThe {self.restaurant_name} is open now\n")

restaurant = Restaurant("ACDC", "chineese")

restaurant.describe_restaurant()
restaurant.open_restaurant()

print(f"Where is {restaurant.restaurant_name} with its {restaurant.cuisine_type.title()} cuisine")

```

```python
# Working with classes and instances
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name          # just return doesnt work
new_car = Car('audi', 'a4', '2024')

print(new_car.descriptive_name())
print(new_car.make)              
```

## Setting a default value for an attribute

When an instance is created, attributes can be defined without being passed in as parameters. These attributes can be defined in the `__init__()` method, where they are assigned a default value.

An attribute called `odometer_reading` that always starts with a value of `0`.
We'll add a method `read_odometer()` that helps us read each car's odometer.
```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0  
        # defining attribute without passing as a parameter

    def descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name

    def read_odometer(self):     # method for reading odometer
        print(f"This car has {self.odometer_reading} miles on it ")

new_car = Car('audi', 'a4', '2024')
print(new_car.descriptive_name())
new_car.read_odometer()
```

## Modifying Attribute Values

Modifying an attribute's value directly
Modifying by changing the attribute directly through an instance
```python
new_car.odometer_reading = 23
# using dot notation to access the car's odometr_reading attribute and set its value. 
```

Modifying an Attribute's value through a method
Instead of accessing the attribute directly, you pass the new value to a method that handles the updating internally.

`def update_odometer(self, mileage):`
Updating it to make sure it cannot be turned back to 0, using conditionals              
  
Incrementing an attribute's value through a method.
not updating it at a time but adding value incrementally using a method to odometer_reading  
`def increment_odometer(self, miles):`    
this can be updated by not allowing negative numbers to not turn back the odometer.

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0  
        # defining attribute without passing as a parameter

    def descriptive_name(self):
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name

    def read_odometer(self):      # method for reading odometer
        print(f"This car has {self.odometer_reading} miles on it ")

# Modifying an Attribute's value through a method
    def update_odometer(self, milage): 
        if milage >= self.odometer_reading:
            self.odometer_reading = milage
        else:
            print("You can't roll back the odometer")

# Incrementing an attribute's value throgh a method
    def increment_odometer(self, miles):
        if miles >= 0:
            self.odometer_reading += miles
        else:
            print("Odometer value cannot be reduced")  

new_car = Car('audi', 'a4', '2024')

new_car.odometer_reading = 23           # direct method
new_car.update_odometer(2345)           # updating throgh method
new_car.update_odometer(12)             # less than actual is not updated
new_car.increment_odometer(-12)         # negative values are not added
  
print(new_car.descriptive_name())
new_car.read_odometer()

  
old_car = Car ('subaru', 'outback', '2017')
old_car.update_odometer(20456)

print(old_car.descriptive_name())
old_car.read_odometer()
```

## Creating points for 2D representation
#20aug24

```python
# 2D points

# __init__() initialises internal values x,y
# first parameter is always self
# Here, default point is at (0,0)
# if p2 = Point() is passed without argument it becomes (0,0) at origin
Class Point:
	def __init__ (self, a=0, b=0):   # __init__ is constructor function
		self.x = a                  # self is identification of itself
		self.y = b

	def translate(self, deltax, deltay):
		self.x += deltax
		self.y += deltay
# Translation: shift a point by (deltax, deltay)
	# (x,y) gives (x + deltax, y + deltay)

	def odistance(self):
		import math
		d = math.sqrt(self.x * self.x + self.y * self.y)
		return(d)
# distance from origin  d = sqareroot of (x^2 + y^2)

# The internals can change but the interface doesnt

	# ___str___()  is an implicit function used by print
	# str(o) == 0.__str()__
	# implication invoked by print() also
	def __ str__(self):
		return( '(' + str(slef.x)+ ',' +str(self.y) + ')' )
	 # returns the values in readable form (x,y)


	def __add__ (self, p):
		return ( Point(self.x + p.x, self.y + p.y) )
		# implicitly invoked by +
	# used to overload operators

	similarly
	__multi__() invoked by *
	__lt__() invoked by <
	__gt__() invoked by >=
	__le__() invoked by <=
```