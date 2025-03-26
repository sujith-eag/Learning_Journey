
1. Describe logical operators and relational operators in python with suitable examples.

An **operator** is a symbol that performs an operation on one or more operands (variables or values).

Logical operators are used to combine conditional statements. They are commonly used in `if` statements to handle multiple conditions.

Operators: `and`, `or`, `not`
- `and`: Returns `True` if both operands are `True`
- `or`: Returns `True` if at least one operand is `True`
- `not`: Reverses the boolean value (returns `True` if the operand is `False`, and vice versa)
```python
x = True
y = False
print(x and y)  # False
print(x or y)   # True
print(not x)    # False
```

Relational (or comparison) operators are used to compare two values. They return a boolean value (`True` or `False`). Operators: `>`, `<`, `==`, `!=`, `<=`, `>=`

- **`>`**: Greater than
- **`<`**: Less than
- **`==`**: Equal to
- **`!=`**: Not equal to
- **`<=`**: Less than or equal to
- **`>=`**: Greater than or equal to

```python
x = 10
y = 20
print(x < y)  # True
print(x == y) # False
print(x != y) # True
```

Relational operators can also be chained. If any condition is `False`, the result will be `False`.

```python
# Example of chaining:
print(5 < 10 < 20)  # True
print(10 < 5 < 20)  # False
```



2. Write a python script to demonstrate `if..elif...else` statement in python.

`if...elif...else` are the primary structures for controlling the flow of execution based on conditions.

`if`, `elif`, `else` – Conditional execution of code blocks based on boolean expressions. Python checks each condition in order, and once one condition is true, it skips the rest:

```python
x, y = 3, 4

if x < y:
    print("x is less than y")
elif x > y:
    print("x is greater than y")
else:
    print("x is equal to y")
```

```python
x = 3

if x == 1:
    y = f1(x)
elif x == 2:
    y = f2(x)
elif x == 3:
    y = f3(x)
else:
    y = f4(x)
```

```python
name = input("What is your name? ")

if name == "Harry" or name == "Hermione" or name == "Ron":
    print("Gryffindor")
elif name == "Draco":
    print("Slytherin")
else:
    print("Who?")
```


3. Demonstrate the usage of pass, break and continue statement in python using suitable examples.

- `break` – Exits the loop immediately.
- `continue` – Skips the rest of the current loop iteration and moves to the next iteration.
- `pass` – Does nothing; used as a placeholder.

```python
prompt = "\nEnter the city you have visited:"
prompt += "\nUse 'quit' to exit. "

while True:
    city = input(prompt)
    if city == "quit":
        break  # Exits when 'quit' is entered
    else:
        print(f"\n{city.title()} is lovely")
```

```python
number = 0

while number < 10:
    number += 1
    if number % 2 == 0:  # Skips even numbers
        continue
    else:
        print(number)  # Prints only odd numbers
```

___

4. Describe membership operator and identity operator in python with suitable examples.

Membership operators are used to check if a value is present in a sequence (like a string, list, tuple, etc.).

Operators: `in`, `not in`
- `in`: Returns `True` if the value is found in the sequence
- `not in`: Returns `True` if the value is not found in the sequence
```python
fruits = ['apple', 'banana', 'orange']
print('apple' in fruits)    # True
print('grapes' not in fruits)  # True
```

Identity operators are used to compare the memory locations of two objects. These operators help check if two variables point to the same object in memory.

Operators: `is`, `is not`
- `is`: Returns `True` if both operands refer to the same object in memory
- `is not`: Returns `True` if both operands do not refer to the same object

```python
x = [1, 2, 3]
y = [1, 2, 3]
z = x
print(x is y)    # False (different objects in memory)
print(x is z)    # True (same object in memory)
```


4. Give the syntax of range() function and discuss its importance. Write a python script to demonstrate for loop statement with range() function.

The `range()` function generates a sequence of numbers, commonly used for looping or generating lists with specific patterns.

- `range(j)` Starts from `0` and ends before `j`. This is equivalent to `range(0, j)`.
```python
range(j)
# Like slice(:j), starts from 0, ends at j-1
```

- `range(i, j)` Generates a sequence of numbers starting from `i` and ending before `j`.
```python
range(i, j)
# Produces the sequence: i, i+1, ..., j-1
```

- `range(i, j, k)`  
Adds an optional third argument `k` for defining the step increment, useful for sequences with a specific pattern, like arithmetic progressions (AP).
```python
range(i, j, k)
# Produces: i, i+k, i+2k, ..., i+nk
```

```python
def factors(n):
	flist = []
	for i in range(1, n + 1):
		if n % i == 0:
			flist.append(i)  
			# Or flist = flist + [i]
	return flist
```


5. Demonstrate the usage of while statement in python. Write a python script to demonstrate while concept to add 5 numbers.

```python
list_1 = [2,4,6,8,10]
number = 0
total = 0
while number < 5:
	total += list[number]    
    number += 1

print(total)
```
