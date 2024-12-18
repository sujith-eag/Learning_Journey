
#### Disk Buffers
Disk data is read/write in large blocks, "Buffer" is a temporary parking place for disk data.
Open a file - create a file handle to file on disk. Like setting up a buffer for the file and getting access to it.

All read and write operations are done on the file handle.

Close a file - Write out the buffer to disk (flush).
	disconnect file handle.

`hf = open("gcd.py", "r")`

First argument to "open" is file name
	can give full path
Second argument is mode for opening file
	Read, "r": opens a file for reading only
	Write, "w": creates an empty file to write to (overwrites if file already exists)
	Append, "a": append to an existing file


```python
# Read through file handle
hf = open("gcd.py", "r")
contents = hf.read()     # reads entire file into name as a single string

contents = hf.readline()
	# reads one line into name - and line ends with '\n'

contents = hf.readlines()
	# reads entire file as list of strings
		# each string is one line ending with '\n'
		
hf.seek(n) # moves the pointer to positions n

block = fh.read(12) # reads a fixed numner of characters, 12 character blocks

# reading a file is sequential operation,
	# when file is opened, point to possition 0 as start
	# Each successive readline() moves forward to '\n' as end of that string

# end of file when 
hf.read() returns empty string ""
hf.readline() returns empty string ""
```

# Handles for Writing & Closing
```python
# writing to a file
fh.write(s)
	# write string s to a file
		# '\n' should be included explicitly to go to new line
		# Returns mumber of characters written (to identify if disk was full)

fh.writelines(l)
	# write a list of lines l to file 
		# '\n' should be included explicitly for each line


# Closing a file
fh.close()
	# Flushes output buffer and decouples file handle
		# all pending writes copied to disk

fh.flush()
	# Manually forces write to disk (doesnt close the file)
```

# File Processing
```python
# Processing file line by line
contents = fh.readlines()
for l in contents:
	. . .
# or making it one line
for l in fh.readlines()
	. . .


# copying a file to another, line by line
infile = open("input.txt", "r")
outfile = open("output.txt", "w")

for line in infile.readlines():
	outfile.write(line)

infile.close()
outfile.close()


# copying a file to another, in one go
infile = open("input.txt", "r")
outfile = open("output.txt", "w")

contents = infile.readlines()
outfile.writelines(contents)

infile.close()
outfile.close()
```

## Strip new line(\n) character
```python
# Get rid of trailing '\n'

contents = fh.readlines()
for line in contents:
	s = line[ :-1]  # \n is last charcter, so taking slice upto last character

# Using rstrip() to remove trailing whitespace from a string, also \n
for line in contents:
	s = line.rstrip()
	
# also strip() for both sides,
# lstrip() from left side

```

## To notice
```python
input.txt is 
The quick brown
fox
jumps over the lazy dog.
```

```python
f = open("input.txt", "r")
for line in f.readlines():
	print(line)
```

```
# print will add \n, readline will also add \n
The quick brown

fox

jumps over the lazy dog.
```

If immediately read line again, it will return empty string as the sequential reading of file is over and pointer is at the end of the file.

If file is closed and and read, it will show error as file is not opened

```python
f = open("input.txt", "r")
for line in f.readlines():
	print(line, end="")    # will remove extra new lines
```

```python
# Reading from a file

from pathlib import Path

path = Path('py_digits.txt')
contents = path.read_text().rstrip()
print(contents)
```

## Relative and Absolute File Paths

A relative file path tells Python to look for a given location relative to the directory where the currently running program file is stored.

When you pass a simple filename like py_digits.txt to Path, Python looks in the directory where the file that's currently being executed (that is, your .py program file) is stored.

To get Python to open files from a directory other than the one where your program file is stored, you need to provide the correct path.

Since text_files is inside python_work, we need to build a path that starts with the directory text_files, and ends with the filename. Here's how to build this path: path = Path('text_files/filename.txt')

You can also tell Python exactly where the file is on your computer, regardless of where the program that's being executed is stored. This is called an absolute file path.

Absolute paths are usually longer than relative paths, because they start at your system's root folder:
`path = Path('/home/eric/data_files/text_files/filename.txt')`

```python  
# Accessing a File's Lines
You can use the splitlines() method to turn a long string into a set of lines, and then use a for loop to examine each line from a file, one at a time:


from pathlib import Path

path = Path('py_digits.txt')
contents = path.read_text()

lines=contents.splitlines()

for line in lines:

    print(line)
```

### Working with a File's contents
```python
from pathlib import Path

path = Path('py_digits.txt')
contents= path.read_text().rstrip()
lines = contents.splitlines()
pi_string = ''

for line in lines:
    pi_string += line.lstrip()

print (pi_string)
print (len(pi_string))


""" When Python reads from a text file, it interprets all text in the file as a string. If you read in a number and want to work with that value in a numerical context, you'll have to convert it to an integer using the int() function or a float using the float() function."""

# to print a limited no of digits in a file with large number of digits
# print (f"{pi_string[:20]}....")  

```

```python
You can use the replace() method to replace any word in a string with a different word.
Here's a quick example showing how to replace 'dog' with 'cat' in a sentence:

>>> message = "I really like dogs."
>>> message.replace('dog', 'cat')
'I really like cats.'


""" Simpler Code: 
The program file_reader.py in this section uses a temporary variable, lines, to show how splitlines() works. You can skip the temporary variable and loop directly over the list that splitlines() returns: """

for line in contents.splitlines():
```

### Writing to a file
```python
from pathlib import Path

contents = "I love programming.\n"
contents += "I love creating new games.\n"
contents += "I love working with data.\n"

path = Path('prog.txt')
path.write_text(contents)


""" 
The write_text() method does a few things behind the scenes. If the file that path points to doesn't exist, it creates that file. Also, after writing the string to the file, it makes sure the file is closed properly.

# Files that aren't closed properly can lead to missing or corrupted data.

# Be careful when calling write_text() on a path object. If the file already exists, write_text() will erase the current contents of the file and write new contents to the file. """
```
# Handling Exceptions
```python
print("Give me two numbers, i'll divide them")
print ("Enter 'q' to quit")

while True:
    first_no = input("\nFirst Number: ")
    if first_no == "q":
        break

    second_no = input("\nSecond Number: ")
    if second_no == 'q':
        break
  
    try:
        answer = int(first_no) / int(second_no)
    except ZeroDivisionError:
        print("You cannot divide by zero")
    else:
        print (answer)
  

""" The only code that should go in a try block is code that might cause an exception to be raised.

Sometimes you'll have additional code that should run only if the try block was successful; this code goes in the else block.

The except block tells Python what to do in case a certain exception arises when it tries to run the code in the try block.

By anticipating likely sources of errors, you can write robust programs that continue to run even when they encounter invalid data and missing resources. Your code will be resistant to innocent user mistakes and malicious attacks"""
```

# Analyzing texts
```python
from pathlib import Path

path = Path('alice.txt')
contents = path.read_text(encoding='utf-8')
words = contents.split()
num_words = len(words)
print (f"The file {path} has about {num_words} words.")


from pathlib import Path

path = Path('alice.txt')
try:
    contents = path.read_text(encoding='utf-8')
except FileNotFoundError:
    print( f"Sorry, the file {path} does not exist.")
else:
    words = contents.split()
    word_count = len(words)
    print = (f"The file {path} contains {word_count} words.")

  
  
from pathlib import Path

def count_words(path):
    Count the appropriate number of words in a file
    try:
        contents = path.read_text(encoding = 'utf-8')
    except FileNotFoundError:
        print(f"Sorry, the file {path} doesnt exist.")
    else:
        words = contents.split()
        num_words = len(words)
        print (f"The file {path} has about {num_words} words.")

path = Path('alice.txt')
count_words(path)
```

# to work with multiple files
```python
filenames = ['alice.txt', 'siddhartha.txt', 'moby_dick.txt', 'little_women.txt']
for filename in filenames:
    path = Path(filename)
    count_words(path)  

# Failing silently, Just inform python to nothing in the except block by asking it to pass.
except FileNotFoundError:
   Pass
```

# Storing Data
```python

"""The JSON (JavaScript Object Notation) format was originally developed for JavaScript. However, it has since become a common format used by many languages, including Python."""

#Using json.dumps() and json.loads()

from pathlib import Path
import json

numbers = [2, 3, 5, 7, 11, 13]
path = Path('numbers.json')
content = json.dumps(numbers)
path.write_text(content)
 
  

from pathlib import Path
import json

path = Path('numbers.json')
content = path.read_text()
numbers = json.loads(content)
print(numbers)
```