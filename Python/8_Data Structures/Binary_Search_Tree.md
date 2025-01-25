#25aug24 
## Dynamic Sorted data  

To maintain dynamic data in sorted manner,
Binary search is efficient in sorting once and for all but not to keep the data dynamically sorted regularly when data is changing dynamically

Binary search tree
There is only one copy of a value like a set, no duplicates
For each node with value v
	value in left subtrees are < v
	values in right subtree are > v
			5
		2          8
	1         4             9
	This applies to subtrees (recursive) also 2 has 1 on left 4 on right,   8 has 9 on right

Similar to making a list, the binary search tree has node but with 3 values
One is the contained value, next is pointing to left child, another to right child

A better representation will have a layer of empty nodes on the leaf nodes.
Leaf node has value that is not None, left and right children point to empty nodes all None
Makes it easier to write recursive functions to traverse the tree.

Complexity
All operations on search trees walk down a single path
Worst-case: height of the becomes a single path on one side like a sorted list
Balanced trees: height is O(log n) for n nodes

Trees can be balanced using rotations - look up AVL trees

```c
To find Value V

scan the current node
go left if v is smaller than this node
go right if v is larger than this node
and repeat (a similar generalization of binary search)
```

```python
# Minimum will be on the left most node of the tree, 
# if there are no left nodes then it is the minimal value

def minval(self):
	# assume t is not empty
	if self.left == None:
		return(self.value)
	else:
		return(self.left.minval())

# Maximum - right most node in the tree

def maxval(self):
	# assume t is not empty
	if self.right == None:
		return(self.value)
	else:
		return(self.right.maxval())
```

```python
Inser V
Try to find v,  if it is not present, add it where the search fails

	def insert(self, v):
		if self.isempty():  # add v as a new leaf
			self.value = v
			self.left = Tree()
			self.right = Tree()
			
		if self.value == v:   # value found, do nothing
			return
			
		if v < self.value:
			self.left.insert(v)
			return
			
		if v > self.value:
			self.right.insert(v)
			return
```

```python
Delete v

If v is present, delete it
if deleted node is a leaf, done
if deleted node has only one child, "promote" that child
if deleted node has two children, fill in the hole with
	self.left.maxval()  or
	self.right.minval()
Delete self.left.maxval() - must be leaf or have only one child

	def delete(self, v):
		if self.isempty():
			return
			
		if v < self.value:
			self.left.delete(v)
			return
			
		if v == self.value:
			if self.isleaf():
				self.makeempty()
			elif self.left.isempty():
				self.copyright()
			else:
				self.value = self.left.maxval()
				self.left.delete(self.left.maxval())
			return
```

```python
# Empty node has self.value, self.left, self.right = None
# Leaf has self.value != None, and self.right, self.left point to empty node

# Constructor: creates an empty node or a leaf node, depending on interval

class Tree:

	def __init__(self, initval = None):
		self.value = initval
		if self.value:
			self.left = Tree()
			self.right = Tree()
		else:
			self.right = None
			self.left = None
		return
	
	# Only empty nodes have value None
	def isempty(self):
		return(self.value == None)
		
	# Leaf node has value None
	def isleaf(self):
		return(self.left.isempty() and self.right.isempty())
	
	# Convert a leaf node to an empty node
	def makeempty(self):
		self.value = None
		self.right = None
		self.left = None
		return
	
	# Copy right child values to current node
	def copyright(self):
		self.value = self.right.value
		self.left = self.right.left
		self.right = self.right.right
		return

	# Check if value v occurs in tree
	def find(self, v):
		if self.isempty():
			return(False)
			
		if self.value == v:
			return(True)
			
		if v < self.value:
			return(self.left.find(v))
			
		if v > self.value:
			return(self.right.find(v))
	
	# Insert value v in tree
	def insert(self, v):
		if self.isempty():  # add v as a new leaf
			self.value = v
			self.left = Tree()
			self.right = Tree()
			
		if self.value == v:   # value found, do nothing
			return
			
		if v < self.value:
			self.left.insert(v)
			return
			
		if v > self.value:
			self.right.insert(v)
			return
		
	# Find maximum value in a nonempty tree
	def maxval(self):
		if self.right.isempty():
			return(self.value)
		else:
			return(self.right.maxval())
	
	# Delete value v from tree
	def delete(self, v):
		if self.isempty():
			return
			
		if v < self.value:
			self.left.delete(v)
			return
			
		if v == self.value:
			if self.isleaf():
				self.makeempty()
			elif self.left.isempty():
				self.copyright()
			else:
				self.value = self.left.maxval()
				self.left.delete(self.left.maxval())
			return
			
	# Inorder traversal
	def inorder(self):
		if self.isempty():
			return([])
		else:
			return (self.left.inorder() + [self.value] + self.right.inorder())
			
	# Display Tree as a string
	def __str__(self):
		return(str(self.inorder()))
```

