
On and off of a bit (binary digit),
to using combination of bits to represent a particular integer or character as bit map.
`000 001 010` with just three bits 8 versions can be made which can represent numbers from 0 to 7.

Any assignment is valid as long as no integers are assigned to the same bit setting.

#### Binary & Decimal integers

ones compliment to represent a negative value.
twos complement notation where 1 is added to the ones complement representation of a negative number.

The usual method used by computers to represent real numbers is floating point notation which can be used to represent very large or small values.

Character Strings
Information is not always interpreted numerically.

The number of bits necessary to represent a character in a particular computer is called the `byte size` and the group of bits of that number is called `byte`.

Any information by itself has no meaning, any meaning can be assigned to a particular bit pattern, as long as it is done consistently.

___

> A new concept on Data Type

The bit string `00100110` can be interpreted as the number 38(binary), the number 26(binary coded decimal) or the character `&`.
A method of interpreting a bit pattern is called ***data type***.

The various `data` type presented were, binary integers, binary coded decimal, non negative integers, real numbers and character strings.
The question would be how to know what data types are available and which ones should be used to to interpret a particular type of data.

___

***Hardware and Software***

Memory is a group of bits which is in a particular state at any time.
The bits are grouped together into larger units called words or larger words.

Each such byte or word has an address to identify it which will be numeric.
Address is often called as the location, and the contents of the location are the values of the bits that make up the unit at that location.

> Points on declaring types and pointers

Every computer has a set of "native" data types.
It is basically the computer knowing how to handle the data at the given location as binary integer or real number.
So two separate instructions are necessary for the two operations and each instruction carries within itself an implicit identification for the type of its operands as well as their explicit location.

```c
int x, y;
float a, b;

x = x + y;
a = a + b;
```
Here the identifiers for the locations may be `x, y, a, b` which is used instead of the numeric address to refer to a particular address as a convenience.

Locations reserved for `x, y` are interpreted as integers, hence the compiler will translate the `+` into integer addition. and for `a + b` it will turn it into floating point addition.

`+` is like a generic operator because it has several meanings depending on its context.
This relieves the programmer of specifying the type of addition to perform.

Declaration specifies how the contents of the specific memory are interpreted by the program. also how much memory is needed for a particular entity,
also specify to the compiler exactly what is meant by the operation symbols that are subsequently used.

___

***Concept of implementation***

Once the concept of "data type" is divorced from the hardware capabilities of the computer, a limitless number of data types can be considered.

> A data type is an abstract concept defined by a set of logical properties

Once such an abstract data type is defined and the legal operations are specified, we may implement the data type.

Implementation might be `hardware implementation` or `software implementation`

A software implementation includes a specification of how an object of the new data type is represented by objects of previously existing data types,
as well as specification of how such an object is manipulated in conference with the operations defined for it.

`MOVE (source, dest, length)`
`length` must be an integer, `dest` `source` can be identifiers that represent the storage locations.
`MOVE(a,b,3)`
each plays a different role,
first operand of `MOVE` instruction is the contents of the location specified by the identifier a.
The second operand is not the contents of the location b, since it is irrelevant for the execution of the instruction. The location itself becomes the operand.

> Although an identifier always stands for a location, it is common for an identifier to be used to refer to the contents of the location. 

`z = x + y`
computer hardware interprets the contents of the bytes at locations `x` and `y` as binary integers, adds them.
`z` is used to refer the memory location for the binary representation of the sum to be inserted into.

The proper interpretation is clear from the context.

(PAGE 25)

> List indexing

Sometimes it is desirable to add a quantity to an address to obtain another address.
If `a` is location in memory, we might want to reference a location four bytes beyond `a`. 
It cannot be `a+4` as it is reserved for the integer contents of location `a+4`.

Therefore we introduce the notation `a[4]` to refer to this location.
notation `a[x]` to refer to the address given by adding the binary integer contents of the byte at `x` to the address `a`.


`MOVEVAR(source, dest)` implementation using `MOVE(source, dest, length)`
All strings are terminated by the special character `\0` which is automatically placed by the compiler at the end of every string.
Since the length of the string is not known in advance, all the string operations must proceed a character at a time until `\0` is encountered.

```c
i = 0;
while (source[i] != '\0') {
	MOVE(source[i], dest[i], 1);
	i++;
}
dest[i] = '\0';
/* terminate the destination string with '\0' */
```



***Abstract Data Types***
(page 30)
Fundamentally a data type is a collection of values and a set of operations on those values.

The term "abstract data type" refers to the basic mathematical concepts that define the data type. A useful tool for specifying the logical properties of a data type is `abstract data type` or `ADT`.

By defining a ADT as a mathematical concept we are not concerned with the space and time complexity or the implementation also, it may not be universally implementable also.
Nevertheless, by specifying mathematical and logical properties of a data type or structure, the ADT is a useful guideline to implementors and a useful tool to programmers who wish to use the data type correctly.


