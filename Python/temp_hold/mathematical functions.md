
Math module

### Constants in math module

`pi`
`e`
`inf` a floating point possitive infinity , for negative infinity, use `-math.inf`. equivalent to `float('inf')`
`nan` a floating point "not a number" value equivalent to `float('nan')`

### Functions

it contains special functions for mathematical operations
```python
>>> import math
>>> math.sqrt(16)
4.0

>>> import math as m
>>> m.sqrt(16)
4.0

>>> from math import sqrt
>>> sqrt(16)
4.0

>>> from math import factorial, sqrt
>>> factorial(10)
3628800
>>> sqrt(16)
4.0
```

`celi(x)`  round up decimal
 `floor(x)` round down  decimal
`fabs(x)`   abolute value (positive quantity ) of x

`trunc(x)` just the real value of a float
`modf(x)` return the integer and decimal value of a number separately
```python
>>> m.modf(13.2)
(0.1999999999999993, 13.0)
>>> m.modf(13.5)
(0.5, 13.0)
>>> 
```

`fnan(x)`  true of x is not a number
`isinf(x)` true if x is a possitive or negative infinity. `float(Inf)`
```python
>>> x = float('inf')
>>> m.isinf(x)
True

>>> x = m.inf
>>> m.isinf(x)
```

`fmod(x,y)`  returns remainder from division of x and y.  it is prefered over `%` for calculating float value 
`fsum(values)`  return the accurate value of floating point values.

`pow(x,y)` x raised to power y
`sqrt(x)`  positive square root
`factorial(x)`  
`gcd(x,y)` greatest common divisor of x and y.
`exp(x)` -  `e **x`

 `degrees(x)`  angle from radian to degrees
`radians(s)` degree to radians


`sin(x)` `cos` `tan` 


___

Area of a circle

```python
>>> import math as m

>>> r = 10
>>> area = m.pi * pow(r, 2)
>>> area
314.1592653589793

>>> r = 15.5
>>> area = m.pi * pow(r, 2)
>>> area
754.7676350249478
```