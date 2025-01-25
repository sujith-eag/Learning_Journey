
### Features of Python
- Simple, easy to learn, and open source
- High-level language, dynamically typed, platform-independent
- Portable
- Supports both procedural and object-oriented programming
- Interpreted
- Extensible
- Embeddable
- Has a huge standard library
- Scripting language
- Database connectivity
- Scalable
- "Batteries included" (comes with many built-in modules)

---

### Source Code to Execution Flow
1. **Source Code** → **Compiler**  
2. **Byte Code** → **Interpreter (PVM)**  
3. **Machine Code** → **Computer**

---

### Executable Files and Frozen Binaries
- `.pyc` files (compiled Python files) with associated libraries.
- Tools for creating standalone executables:
  - `py2exe`
  - `pyinstaller`
  - `freeze`

---

### Memory Management
- Python uses an **object-specific allocator**, relying on:
  - **Python's raw memory allocator**
  - The **OS memory allocator**
  - **RAM**

---

### Garbage Collection
- Functions related to garbage collection:
  - `get_threshold()`  
  - `collect()`  
- Garbage collection is **time-based** and **event-based**.

---

### Inline Assignment Using the Walrus Operator (from Python 3.8 onwards)

In **C**:
```c
while( (n = get_number()) != -1 )
```

In **Python**:
```python
while ( (n := len(my_list)) > 10 ):
```

---
