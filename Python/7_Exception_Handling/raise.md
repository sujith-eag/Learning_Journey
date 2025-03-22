

User Defined Exceptions

```
class NegativeNumberError(Exception):
	pass

num = -5
if num < 0;
	raise NegativeNumberError("Negative Numbers not allowed")
```

```
class CustomError(Exception):
	pass

try:
	raise CustomError("This is a custom Exception!")
except CustomError as e:
	printf(f"caught a erroe: {e}")
```

