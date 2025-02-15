
list of **all functions** in the `functools` module in Python, along with brief explanations, examples, and use cases for each one:

### 1. **`functools.reduce()`**

- **Purpose:** Applies a binary function cumulatively to the items of an iterable, reducing it to a single value.
- **Use Case:** When you need to accumulate values, like multiplying all numbers in a list.
- **Example:**

```python
from functools import reduce

lst = [1, 2, 3, 4, 5]
result = reduce(lambda x, y: x * y, lst)
print(result)  # Output: 120
```

- **Use Case:** Calculating the product of all numbers in a list.

---

### 2. **`functools.partial()`**

- **Purpose:** Creates a new function with some arguments of the original function fixed (function currying).
- **Use Case:** When you want to fix certain arguments in a function ahead of time.
- **Example:**

```python
from functools import partial

def power(base, exp):
	return base ** exp

square = partial(power, exp=2)
print(square(5))  # Output: 25
```

- **Use Case:** Pre-configuring a function with default values.

---

### 3. **`functools.lru_cache()`**

- **Purpose:** Caches results of expensive function calls to avoid redundant computations.
- **Use Case:** Useful for optimizing functions that have repetitive computations (e.g., recursive algorithms).
- **Example:**

```python
from functools import lru_cache

@lru_cache(maxsize=None)  # No cache limit
def fibonacci(n):
	if n <= 1:
		return n
	return fibonacci(n - 1) + fibonacci(n - 2)

print(fibonacci(100))
```

- **Use Case:** Memoizing Fibonacci numbers to avoid recalculating already computed values.

---

### 4. **`functools.wraps()`**

- **Purpose:** Decorator to preserve the metadata (like `__name__` and `__doc__`) of the original function when it's wrapped by another function.
- **Use Case:** When creating custom decorators that should not obscure the original function's attributes.
- **Example:**

```python
from functools import wraps

def my_decorator(func):
	@wraps(func)
	def wrapper(*args, **kwargs):
		print(f"Calling {func.__name__}")
		return func(*args, **kwargs)
	return wrapper

@my_decorator
def greet(name):
	"""Greet a person"""
	print(f"Hello {name}")

print(greet.__name__)  # Output: greet
print(greet.__doc__)   # Output: Greet a person
```

- **Use Case:** Ensuring that decorators don’t interfere with the original function's metadata.

---

### 5. **`functools.total_ordering()`**

- **Purpose:** A class decorator that simplifies writing rich comparison methods by defining one or two of the comparison methods (`__lt__`, `__le__`, `__gt__`, `__ge__`, `__eq__`, `__ne__`).
- **Use Case:** Simplifies class definitions by auto-generating comparison methods.
- **Example:**

```python
from functools import total_ordering

@total_ordering
class Point:
	def __init__(self, x, y):
		self.x, self.y = x, y

	def __eq__(self, other):
		return (self.x, self.y) == (other.x, other.y)

	def __lt__(self, other):
		return (self.x, self.y) < (other.x, other.y)

p1 = Point(1, 2)
p2 = Point(2, 3)
print(p1 < p2)  # Output: True
print(p1 == p2)  # Output: False
```

- **Use Case:** Simplifying comparison logic in custom classes.

---

### 6. **`functools.cached_property()`**

- **Purpose:** Converts a method into a property that is computed once and then cached.
- **Use Case:** Used for properties that are expensive to compute but should be recomputed only when necessary.
- **Example:**

```python
from functools import cached_property

class Circle:
	def __init__(self, radius):
		self.radius = radius

	@cached_property
	def area(self):
		print("Computing area...")
		return 3.14 * self.radius ** 2

c = Circle(5)
print(c.area)  # "Computing area..." and the computed area
```

- **Use Case:** Optimizing frequently used properties that do not change often.

---

### 7. **`functools.singledispatch()`**

- **Purpose:** Used to define a generic function, and allow for function overloading based on the type of the first argument.
- **Use Case:** Defining a function that can behave differently based on the type of its first argument.
- **Example:**

```python
from functools import singledispatch

@singledispatch
def func(arg):
	print("Default function")

@func.register(int)
def _(arg):
	print(f"Function for int: {arg}")

@func.register(str)
def _(arg):
	print(f"Function for str: {arg}")

func(10)  # Output: Function for int: 10
func("hello")  # Output: Function for str: hello
```

- **Use Case:** Overloading a function based on the argument type.

---

### 8. **`functools.identity()`**

- **Purpose:** A simple function that returns the argument unchanged.
- **Use Case:** Often used in situations where a default identity function is needed (e.g., when passing a function as an argument).
- **Example:**

```python
from functools import identity

print(identity(10))  # Output: 10
```

- **Use Case:** Used in higher-order functions where no transformation is required.

---

### 9. **`functools.cache_property()`**

- **Purpose:** It is a decorator that transforms a method into a property that caches its result.
- **Use Case:** When you need to cache the result of an expensive calculation in a class, but want it to only be computed once.
- **Example:**

```python
from functools import cache_property

class HeavyComputation:
	@cache_property
	def result(self):
		print("Calculating...")
		return 42

obj = HeavyComputation()
print(obj.result)  # First call, it prints "Calculating..." and returns 42
print(obj.result)  # Cached, no "Calculating..." message
```


---

### 10. **`functools.cache_clear()`**

- **Purpose:** Clears the cache for a cached property or method.
- **Use Case:** When you want to invalidate cached data after certain conditions have changed.
- **Example:**

```python
from functools import cache_clear
```


---

### Summary Table of `functools` Functions:

|Function|Description|Example Use Case|
|---|---|---|
|`reduce()`|Applies a function cumulatively to the iterable.|Multiplying numbers in a list.|
|`partial()`|Fixes certain arguments of a function ahead of time.|Pre-configuring a function (currying).|
|`lru_cache()`|Caches results of function calls to improve performance.|Memoizing results of recursive functions.|
|`wraps()`|Preserves metadata of the original function in decorators.|Writing decorators that don’t lose metadata.|
|`total_ordering()`|Simplifies writing rich comparison methods.|Auto-generating comparison methods in classes.|
|`cached_property()`|Turns a method into a cached property.|Caching an expensive property calculation.|
|`singledispatch()`|Defines a generic function with function overloading.|Function overloading based on argument type.|
|`identity()`|Returns the argument unchanged.|Identity function used in higher-order functions.|

### Conclusion:

`functools` provides many powerful tools for functional programming, caching, and optimization in Python. Depending on your needs, you can leverage `partial()` for function currying, `lru_cache()` for optimizing expensive functions, `wraps()` for maintaining function metadata, and many other tools to enhance your Python applications.

Let me know if you'd like more in-depth examples or clarifications on any of these!