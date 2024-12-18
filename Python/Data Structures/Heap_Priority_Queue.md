#22aug24 

# Priority Queues and Heaps 

Need to maintain a list of jobs with priorities to optimise the following operations

* delete_max()
	Identify and remove(pick) job with highest priority
	There is no need for it to be unique

* insert()
	Add new job to the list


```c
Ex: Job scheduler
A job scheduler maintains a list of pending jobs with their priorities.

When the processor is free, the scheduler picks out the job with maximum priority in the list and schedules it.

New job may join the list at any time

How the scheduler should maintain a list of pending jobs and their priorities?
```

### Using Linear structures for a priority Queue
```c
* Unsorted list
	* insert() takes O(1) time
	* delete_max() takes O(n) time

* Sorted list 
	* delete_max takes O(1) time
	* insert() takes O(n) time

So in whatever way, processing a job requires O(n^2) time
which is the limitation of keeping data in one dimentional (linear) structure
```

## Binary tree
```c
Most basic two dimentional structure.

Each node has value stored in it, with possibly a left and a right child (with at most two nodes attached)

Root is the top of the tree, 
each node having one or two children(left and right child)
Parent nodes are ones above those nodes
Leaf is the Node with no children
```

## Priority Queue as trees (Heap)
```c
Heap is a balanced tree
	balanced means in rough sense the left and the right are same size
Since the number of nodes doubles every level, the hight of the tree with N nodes will be of the order log N.

When height is (log N), the insert and delete will happen in (log N) time and both will happen in (N log N) instead of O(N^2)

N need not be fixed also, as heap grows and shrinks
```

# Heap
```c
Is a balanced tree, with certain restrictions and rules

> It is filled level by level (cant fill next level before completing previous)
> It is filled from left to right (at the last level all filled values are on the left and empty ones are on the right)
> At each node, the values stored in the parent node must be bigger than the child node (bigger child element cannot be attached to a lesser parent node)
```

## Insert( )
```c
Possition of new node is fixed by structure

suppose the child node is bigger than node above, exchange,
if still there are bigger ones above, exchange till the heap properties are restored.
(there is no need to check the ones beside a node, they do not matter as they will anyway be smaller)


# Complexity of Insert()

We only walk up a path, never down a path.
So the number of steps we walk up is bounded by the hight of the tree.

number of nodes at level 0,1,..i   is  2^0, 2^1,...2^i

when k levels are filled:  2^0 + 2^1 + ..+ 2^(k-1) = 2^k - 1

flipping this, for N nodes: number of levels at most is  log N + 1

so insert takes O(log N)
```

## delete_max( )
```c
Maximum value are always at the root, so when the value is removed,
the root node is empty.
at the bottom, due to heap structural constraint, the last element/node from at the right end also need to be removed.

so now the homeless value/element removed at the leaf is moved to the root node.

since it will be smaller than its children, it is swapped with the largest child and this is continued till the structure of heap becomes right.

This will alse follow a single path from root so the cost is bound by hight of the tree and time will be O(log N)
```

## Implementing Heap using array/list
```c
The numbering of nodes goes from left to right, level by level woth 2 child each

		   0
	1		      2
 3       4     5	      6
7  8   9  10  11  12    13   14

0 index forms the root and 1 2 its children and so on.

if H[0,..n-1] represents a heap

for any number at H[i], the children are present at  H[ 2i+1 ]  H[ 2i +2 ]
ex: for 3  children are [2*3+1] = 7  and  [2*3+2] = 8

for parents, just the reverse
parent of H[i]  is at  H[ floor((j-1)/2) ]
	oh there is one parent for two children
	the floor() is taken to remove fraction
ex : parent of 11   is  floor((11-1)/2)  = 5
	parent of 12 is  floor( (12-1)/2) = floor(5.5) = 5

this allows us to manipulate parent and children nodes by doing index arithmatics
```

## Building a heap, heapify( )
```c
Naive Strategy

Given a list of values [x1, x2, . . ., xn] to build a heap
start with an empty heap, starting from the top,
insert each xj one by one and the overall complexity will be O(N log N)
```

```c
Better heapify()

set up the array as [x1, x2, . . ., xn]
	In this list half of the elements will become the leaf, so this second half of the array trivially satisfy heap property (will not have any child node, and will be filled from left to right)
so second half is already a heap.

assuming the leaf nodes are at level k
	for each node at level k-1, k-2,...0 till root, the heap property has to be fixed ( swapping the lower and higher)
	
	as we go up, the number of steps per node goes up by 1 for an extra layer.
	but the number of nodes per level gets halved.

Cost of building this heap will be O(N) overall

ex: 
7,8,9,10,11,12,13,14 are 8 nodes from left to right form the bottom leafs which is 14/2 of 14 elements in a list.

3,4,5,6  are the 4 nodes above it, as these are added, 1 swap might happen each

1,2 are added on top and swapped 2 times if smaller

0 will form the root node and swapped max of 3 times
```

# Heap sort
```c
Starting with an unsorted list
building a heap - O(n)

calling delete_max() n times to extract each elements in descending order - so will be O(n log n)

To store the removed value from the heap there will not be any need of another array.
The heap itself is made in an array with the root at 0 and leaf at -1

when delete_max is called, element at 0 is removed, the number of elements shrinks by 1, and the element at last node(-1 possition) moves to 0, now -1 place becomes empty.

so the largest element removed from 0 is shifted to -1, and that possition is not considered for further sort.

when next big element is removed from 0, it is shifted to -2 place and in this way the list is sorted in assending order.

This in place takes O(n log n) similar to merge and quick sort.  
```

## Min heap
```c
If we invert the heap condition so that parent elements have smaller value than the child node and smallest one is at root, it forms min map.

insert() will work similarly, but in reverse

delete will be delete_min() as the smallest value is removed
```

### Summary
```c
Heaps are a tree mplimentation of priority queues
	Insert() and delete_max() are both O(log n)
	heapify() builds a heap in O(n)
	Trees can be easily manipulated by using an array
	heap sort can sort in place at O(n log n)

by inverting heap conditions min-heap can be made 
```
