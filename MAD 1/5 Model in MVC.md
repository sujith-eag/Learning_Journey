M V C   Paradigm

#### Persistent Storage
Underlying data storage
	persistent - survive server restart
relation representation
structured way to represent and manipulate data


#### Mechanisms for Persistent storage

***keys*** -  In memory data structures, Using unique identifiers for data so there is no confusion and it is more concise.
Combinations of these keys can be further used to represent the relationship between data.
Data entry errors are less likely.
Duplicate will not be a problem with Unique keys.
Easy lookup of data

***Lists or Dictionaries*** can be used also with key value pair to store data

***Defining Objects***  to store data
```python
class Student:
	id_next = 0      # class variable

	def __init__ (self, name, hostel):
		self.name = name
		self.id = Student.idnext
		self.hostel = hostel

		Student.id_next = Student.id_next + 1     # incrementing class variable
```
Setting the object that has to be created allows for automatic Unique id creation by the database and easy retrieval of data.
When it is set as a class, more functionalities can be defined to update and look up data.
New fields can be added easily.

***Making data Persistent***
Data structures are lost when server is shut down or restarted

This can be saved to disk to be read back when restarts
	Python Pickle module
	CSV - comma separated values
	TSV - tab separated values
These work similar to a spreadsheet but will have limited functionality and flexibility.


***Spreadsheet***
Any kind of tabular data expressed in tables which can have multiple inter linked sheets within single spreadsheets.

Two files with different set of data, and
Relationship between data, specified by combining keys from two different columns in a separate table.

Advantages
	Naturally represents tabular data
	Extension, adding fields is easy
	Separate sheet for relationships

Problems
	Look ups, Cross referencing is harder than dedicated database
	Stored procedures - limited functionality
	Atomic operations - no clear definition


# Relational Databases - SQL
from IBM 1970

Data stored in Tabular format
	Columns of tables: fields (name, address, ID )
	Rows of tables: individual entries (student 1, student 2 . . .)

The schema of rows and columns are predetermined and defined, every row in that table will have a same kind of entries.

Key: unique ways of accessing a given row
	Primary key: important for fast access on large databases
	Foreign key: connect to a different table - Relationships

English like, but structured
Quite verbose
Specific mathematical operations:
	Inner join
	outer join


# Unstructured database - NoSQL
Easily add/change fields
Arbitrary data (semi structured or Unstructured data)
NoSQL (MongoDB, CouchDB)
Flexible, but potential loss of validation and search speed





***Model*** is not concerned with how it is displayed in ***view***, it just provides the data.
It will the ***controller*** that has to query and convey how the data has to be displayed.

This background process is separate from the rest of the process, so changing the model behind the scenes will not require changing the other parts. 