

Disk buffers are temporary memory locations used by the operating system to manage file input and output (I/O) operations. These buffers allow efficient reading and writing by minimizing the number of interactions between the program and the disk. When working with files, Python creates a temporary "buffer" that holds data being read or written to a disk. This buffer improves performance by reading and writing data in larger blocks instead of byte-by-byte.

Breakdown of how file handling works in Python, from opening files to reading, writing, and closing them, as well as dealing with file paths.

---

## 1. File Opening and File Handles

When you open a file in Python, the operating system creates a file handle. A file handle provides an interface for interacting with the file. It allows Python to read from or write to the file, and it manages the data in memory before writing it to disk (this is done through the file buffer).

### Opening a File

To open a file, you use the `open()` function, which returns a file handle that you can use to perform operations on the file. The basic syntax is:

```python
hf = open("gcd.py", "r")  # Open the file 'gcd.py' for reading
```

- **First argument**: The filename (can include the full path).
- **Second argument**: The mode in which to open the file:
    - `"r"`: Read-only mode. Opens the file for reading.
    - `"w"`: Write mode. Creates a new file or overwrites an existing file.
    - `"a"`: Append mode. Opens a file for appending (writes at the end of the file without deleting its contents).

---

## 2. Reading Files

Once a file is opened, you can perform various read operations.

### Reading Entire File into a Single String

```python
hf = open("gcd.py", "r")
contents = hf.read()  # Reads the entire file into a single string
```

### Reading One Line at a Time

```python
hf = open("gcd.py", "r")
line = hf.readline()  # Reads one line and stores it in 'line'
```

- `readline()` returns the line including the trailing newline (`\n`).

### Reading All Lines into a List

```python
hf = open("gcd.py", "r")
lines = hf.readlines()  # Reads all lines into a list of strings
```

- Each element in the list is a line from the file, and each line ends with a newline (`\n`).

### Moving the Pointer

```python
hf.seek(n)  # Moves the file pointer to position 'n'
block = hf.read(12)  # Reads the next 12 characters from the current pointer position
```

- The pointer starts at the beginning of the file, and each read operation advances it until the end of the file.

---

## 3. Writing to Files

You can write to a file by opening it in write or append mode. Python provides methods to write data to a file handle.

### **Writing a String**

```python
hf = open("output.txt", "w")
hf.write("Hello, World!\n")  # Writes a string to the file
```

- The `write()` method does not add a newline by default, so you need to add `\n` if you want the data to appear on a new line.

### Writing a List of Lines

```python
lines = ["Hello", "World", "Welcome to Python!"]
hf.writelines(lines)  # Writes each string in the list to the file (does not add \n)
```

### Flushing and Closing a File

When you're done writing, you should close the file to ensure all data is saved and the resources are released.

```python
hf.close()  # Closes the file and flushes the buffer to disk
```

- **`flush()`**: Forces a write operation to the disk without closing the file.
- **`close()`**: Closes the file and ensures all buffered data is written to disk.

```python
hf.flush()  # Ensures any buffered data is written to disk without closing the file
```

---

## 4. File Processing Techniques

### Processing Files Line by Line

You can process large files efficiently by reading and writing them line by line. This way, you don’t load the entire file into memory at once.

```python
hf = open("input.txt", "r")
for line in hf:
    print(line, end="")  # Print the line without adding an extra newline
hf.close()
```

### Copying Files Line by Line

```python
infile = open("input.txt", "r")
outfile = open("output.txt", "w")

for line in infile:
    outfile.write(line)  # Writes each line to the output file

infile.close()
outfile.close()
```

### Copying Files All at Once

If the file is small and can be read all at once, you can use the `readlines()` or `read()` method to load the contents into memory and then write them out in one go:

```python
infile = open("input.txt", "r")
outfile = open("output.txt", "w")

contents = infile.readlines()  # Reads all lines into a list
outfile.writelines(contents)  # Writes the entire list to the file

infile.close()
outfile.close()
```

---

## 5. Stripping Newline Characters

Files often contain newline characters (`\n`) that separate lines. You may want to remove these trailing characters when processing the file’s contents.

### Removing the Trailing Newline

```python
contents = hf.readlines()
for line in contents:
    s = line[:-1]  # Removes the last character (newline) from each line
```

### Using `rstrip()` to Remove Trailing Whitespace

```python
contents = hf.readlines()
for line in contents:
    s = line.rstrip()  # Removes all trailing whitespace, including newlines
```

- **`strip()`** removes whitespace from both ends of a string.
- **`lstrip()`** removes whitespace from the left side of the string.

---

## 6. File Path Management

### Relative vs Absolute File Paths

- **Relative Path**: A relative file path is relative to the directory where the Python script is executed. For example, if your Python file is in `python_work`, and the text files are in a subfolder `text_files`, the relative path would be:

```python
path = Path('text_files/filename.txt')
```

- **Absolute Path**: An absolute path gives the full path starting from the root directory, making it independent of the current working directory. For example:

```python
path = Path('/home/user/data_files/text_files/filename.txt')
```


### Reading Files Using Pathlib

The `pathlib` module allows for easy handling of file paths. You can read a file directly using `read_text()` or `open()` methods.

```python
from pathlib import Path

path = Path('py_digits.txt')
contents = path.read_text()  # Reads the entire file content as a string
print(contents)
```

- **`splitlines()`**: Splits the contents of the file into a list of lines, making it easier to iterate over each line.

```python
from pathlib import Path

path = Path('py_digits.txt')
contents = path.read_text()

lines = contents.splitlines()  # Split the string into lines
for line in lines:
    print(line)
```

---


```python

code = open("trial.py", "r")
content = code.read(40)
print("*"*40)
print("\nRead 40 characters from file\n")
print(content)
print("*"*40)

code.seek(60)
lines = code.read(40)
print("Seeking to 60th point and reading 40 characters\n")
print(f"{lines}")
print("*"*40)



fh = open("empt.c", "w")
fh.write(content)
fh.write("\n")
fh.write(lines)
fh.write("\nGarbage value replacing content")
fh.close()

tr = open("empt.c", "r")
added = tr.read()
print("Opening file for writing,\nWriting three sections, closing\nOpening for reading and printing written values\n")
tr.close()
print(added)


print("*"*40)
print("\nMaking the File Output into a List\n")
tr = open("empt.c", "r")
print(f"\n{tr.readlines()}\n")

fh = open("empt.c", "w")
fh.write("Garbage value replacing content")
fh.close()

tr = open("empt.c", "r")
overwrite = tr.readlines()
fh.close()
print("*"*40)
print("\nFile with content is opened to Write and Overwritten\n")
print(overwrite)
print("*"*40)



fh = open("empt.c", "a")
fh.write("\nAppending this on th earbage value\nwith\\n new line character\n")

print("File Opened for Append, and new sections written\n")
print("\nFile Closed: ", fh.closed)
print("Opening Mode:", fh.mode, "\n")
fh.close()


tr = open("empt.c", "r")
lines = tr.read()
print("\nPrinting the Appended values: \n")
print(lines)
print("\nFile Name: ", fh.name)
print("File Closed: ", fh.closed)
print("\n","*"*40)

```

```
sujith@sujith-Latitude-7490:~/Desktop/labFiles/pylab$ python3 filehandle.py 
****************************************

Read 40 characters from file


import re

email_regex = r'^[a-zA-Z0-9.
****************************************
Seeking to 60th point and reading 40 characters

\.[a-zA-Z]{2,}$'
url_regex = r'^(https?:
****************************************
Opening file for writing,
Writing three sections, closing
Opening for reading and printing written values


import re

email_regex = r'^[a-zA-Z0-9.
\.[a-zA-Z]{2,}$'
url_regex = r'^(https?:
Garbage value replacing content
****************************************

Making the File Output into a List


['\n', 'import re\n', '\n', "email_regex = r'^[a-zA-Z0-9.\n", "\\.[a-zA-Z]{2,}$'\n", "url_regex = r'^(https?:\n", 'Garbage value replacing content']

****************************************

File with content is opened to Write and Overwritten

['Garbage value replacing content']
****************************************
File Opened for Append, and new sections written


File Closed:  False
Opening Mode: a 


Printing the Appended values: 

Garbage value replacing content
Appending this on th earbage value
with\n new line character


File Name:  empt.c
File Closed:  True

 ****************************************
```