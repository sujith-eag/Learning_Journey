
`tuple( )`
can be a string of values
It behaves like a list or string, can extract values.

Used as simultaneous assignments    
`(age, name, primes) = ( 23, "Kamal", [2, 3, 5, 7] )`
  
 can assign a "tuple" of values to a name (similar to a list of values)   
 `point = (3.5,  4.8)`
`date = (16,7,2023)`


Values in position can be extracted, and slices also
`xcoordinate = point[0]`
`monthyear = date[1: ]`

But tuples are immutable (the values cannot be changed in place)
`date[1] = 8` will be an error.