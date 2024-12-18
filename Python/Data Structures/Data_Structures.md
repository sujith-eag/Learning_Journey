
In programming, data structures are fundamental tools used for organizing and storing data efficiently. Different data structures are suited to different types of operations, such as inserting, searching, deleting, and manipulating data. In Python, as in many programming languages, there are several built-in and commonly used data structures. Here’s an overview of the main data structures and some insight into what's missing or less common in Python:

### Commonly Used Data Structures in Programming:

1. **Arrays**:
   - Contiguous memory allocation of elements of the same type. In Python, lists can act similarly to arrays.

2. **Linked Lists**:
   - A sequence of elements where each element points to the next one in the sequence. Python does not have a built-in linked list, but it can be implemented using classes and references.

3. **Stacks**:
   - A Last-In-First-Out (LIFO) data structure where elements are added and removed from the same end. Implemented using lists in Python.

4. **Queues**:
   - A First-In-First-Out (FIFO) data structure where elements are added at the rear and removed from the front. Can be implemented using lists (deque) or collections.deque in Python.

5. **Trees**:
   - Hierarchical data structures with a root value and subtrees of children nodes. Common types include Binary Trees, Binary Search Trees (BST), AVL trees, etc. Python doesn’t have built-in tree data structures but they can be implemented using classes and references.

6. **Graphs**:
   - A collection of nodes (vertices) and edges that connect pairs of nodes. Implemented using dictionaries or custom classes in Python.

7. **Hash Tables** (Dictionaries in Python):
   - Data structures that map keys to values for efficient retrieval. Python dictionaries provide hash table functionality.

8. **Heaps**:
   - Tree-based data structures that satisfy the heap property. Python provides a heapq module for heap operations.

9. **Sets**:
   - Collections of unique elements with operations like union, intersection, difference, etc. Implemented using set class in Python.

### Missing or Less Common Data Structures in Python:

1. **Trie (Prefix Tree)**:
   - A tree-like data structure used for storing a dynamic set of strings. Not built-in, but can be implemented using dictionaries or custom classes.

2. **Skip List**:
   - A probabilistic data structure that allows for fast search, insertion, and deletion operations. Not built-in, but can be implemented using custom classes.

3. **Bloom Filter**:
   - A probabilistic data structure used to test whether an element is a member of a set. Not built-in, but can be implemented using third-party libraries.

4. **Segment Tree**:
   - A tree data structure used for storing intervals or segments and querying information about them. Not built-in, but can be implemented using custom classes.

5. **Radix Tree (Trie)**:
   - A space-optimized trie data structure used to store a set of strings. Not built-in, but can be implemented using custom classes.

Python provides a rich set of built-in data structures that cover most common use cases. For less common or specialized data structures, such as those listed above, Python typically relies on third-party libraries or custom implementations using existing data types like lists, dictionaries, and classes. The flexibility of Python's syntax and its support for object-oriented programming make it feasible to create and use custom data structures effectively when needed.




# Data structures #22aug24

arrays/lists - sequence of values
dictionaries - key value pairs

sets - can be represented as a list with `{ }`, it will not have any identical values/duplicates.
since `{}` is used to declare empty dictionary creating a an empty set is done by using `set()` function. `colours = set()`

`"black" in colours` set membership can be checked 

Converting a list into a set by passing it to set
```python
num = set( [0,1,2,3,4] )
print(num)
# {0,1,2,3,4}
```
A string passed will become set of characters, the order is not preserved (similar to dict), elements are not indexed.

Set supports basic operations
```python
odd = set( [1,3,5,7,9,11] )
prime = set( [2,3,5,7,11] )

Union using   |
odd | prime -> {1,2,3,5,7,9,11}

Intersection  &
odd & prime -> {3,11,5,7}

set difference
odd - prime -> {1,9}
prime - odd -> {2}

Exclusive or     ^    (unique in both)
odd ^ prime -> {1,2,9}
```

#### Stacks
last-in, first-out list

Using in built list as a stack
	stack has a two functions
	`push(s,x)` - add x to stack s
	`pop(s)` - return most recently added element

maintain stack as list, push pop from the right
	`push(s,x)` is  `s.append(x)`
	`s.pop()` - python built-in, returns last element

stacks are natural to keep track of recursive function calls to return to the last function called while going through functions.

In 8 queens, use of stack to keep track of queens added, to push a queen and removing the last one while backtracking.


#### Queues

First in first out of sequences
	`addq(q,x)` - adds x to rear of the queue q
	`removeq(q)` - removes element at head of q

Using lists as queues, left is rear, right as front
	`addq(q,x)` is `q.insert(0,x)`
		`l.insert(j,x)`, inserts x before position j
		`l.insert(0,x)`, puts x at before 0th element
	`remove(q)` is `q.pop()`
Utilization of a queue is to systematically explore through a search space `(nxn grid)`


#### Knight movement (BFS)