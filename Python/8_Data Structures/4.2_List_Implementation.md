
#25aug24

# Implementing lists in python  
## Designing a flexible list
```
List is a sequence of nodes, Each node stores a value and points to the next node.
List L, points to the first node of the list. 
If a node has no pointer[None], it is the end of the list.
Empty list will have both value and pointer as [None].
There will be no [None] in the middle of the list.
A singleton list [v1] will have just a value, pointer at [None]
l = None is not possible, None has no type
```

### Appending to a list
```python
class Node:
	def __init__(self, v = None):  # v is by default None
		self.value = v       # is the stored value
		self.next = None     # points to next node
		return      

	def isempty(self):
		if self.value == None:     # if the value is none it is empty, no value
			return(True)           # l1 = Node()  is empty list
		else:                      # l2 = Node(5) is not empty, singleton list
			return(False)          # L1.isempty() == True, L2.isempty == False

# adding v to end of a list l
	def append(self, v):          # append, recursive
		if self.isempty():        # if l empty, update value from None to v
			self.value = v     
			  
		elif self.next == None:    # if node is at the end, l.next is None
			newnode = Node(v)      # create a new node with v
			self.next = newnode    # Point 'next' pointer to newnode
		else:
			self.next.append(v)  # if middle, recursively append to rest of list
		return
# Another way of appending
# using iterative approace, loop till next is None and add the value
	def append(self, v):         # append, iterative
		if self.isempty():       
			self.value = v      # if empty, replace l.value by v
			return

		temp = self               # loop through l.next till next is not None
		while temp.next != None:  # moving to end of list, temp points at end
			temp = temp.next
		newnode = Node(v)
		temp.next = newnode       # add v at end of list by making new node
		return
```
### Inserting to a list
```python
# We cannot change where l points to (the first node) 
# Inserting value at the start of a list is done by exchanging the value in the first node and new node. 
# L points to first node, first points to new node, new node points to previous second node. (kind of like inserting a node b/w first and second, exchanging the value b/w first and new node) (easy with diagram)
# Now L is pointing to the same node with new value, like it became the first node.

	def insert(self, v):
		if self.isempty():     # if empty append
			self.value = v
			return
			
		newnode = Node(V)
		(self.value, newnode.value) =    # Exchange values in self and newnode
			(newnode.value, self.value)

		(self.next, newnode.next) =      # switch links 
			(newnode, self.next)

		return
```
### Deleting from a list
```python
# deleting a value v (bypassing that value in links, re plumbing)
# to delete v2, make v1 point to v3 bypassing v2 so becomes inaccible

# scan the list for first v -- look ahead at next node
# if next node value is v, bypass it
# if self.next.value == v, bypass self.next
	# self.next = self.next.next    point to one beyond the value to delete
	
# Cannot bypass the first node in the list
	# instead, copy the second node value to head
	# Bypass second node like previous

	def delete(self, v):   # delete, recursive
		if self.isempty():
			return
			
		if self.value == v:     # Value to be deleted
			if self.next == None  # if it is one value, change value to None
				self.value = None
			else:
				self.value = self.next.value  # in first node, not sinleton
				self.next = self.next.next  # swap values, Bypass that value
				return

# finding the first x to delete by walking down the list when v is not in first
		temp = self    
		while temp.next != None:
			if temp.next.value == x:
				temp.next = temp.next.next
				return
			else:
				temp = temp.next
		return

# This is the recursive version of doing when value is not in beginning
		else:              # recursive delete
			if self.next != None:
				self.next.delete(v)
				if self.next.value == None: # checking if next value is None
					self.next = None  # this to handle if last node is deleted
		return
```

### Printing out a list
```python
def __str__(self):
	selflist = []
	if self.value == None:
		return ( str(selflist) )

	temp = self
	selflist.append(temp.value)
	while temp.next != None:
		temp = temp.next
		selflist.append(temp.value)
	return ( str(selflist))
```



