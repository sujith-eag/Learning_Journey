
Abecedarian series - where elements appear in alphabetical order

```python
prefix = "JKLMNOPQ"
suffix = "ack"

for i in prefix:
	print( i + suffix )
```

___

String comparison in python

___

zip() method
takes iterable or containers and returns a single iterator object, having mapped values from all the containers.

`zip(*iterators)`

can be used to combine two or moree lists into pairs (tuples) and the output can be converted into list, dict, tuple or set.
```
zip([1,2,3], [5,6,7])
[(1,5), (2,6), (3,7)]
```

```
name = ["ram", "jai", "raj", "ron"]
age = [25, 41, 50, 20]
print( list(zip(name,age)))

for x,y in zip(name,age):
	print("name",x"and age",y)
```

To unzip

`names, ages = zip(*zipped_list)`
