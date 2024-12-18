# Linear Search
#Linearsearch
Linear search, also known as sequential search, is a straightforward searching algorithm that iterates through a list or array to find a specific element. 
### Algorithm Steps:
1. **Initialization**: Start at the beginning of the list.
2. **Sequential Search**:
   - Compare each element of the list with the target element sequentially.
   - If a match is found, return the index of the element.
   - If the end of the list is reached without finding a match, return a special value (e.g., -1) indicating the element is not present in the list.

### Characteristics of Linear Search:
- **Time Complexity**: O(n), where n is the number of elements in the list. 
- In the worst case, linear search may have to check every element in the list.
 
- **Space Complexity**: O(1), because linear search only requires a constant amount of extra space for variables regardless of the size of the input.

### Use Cases:
- **Unsorted Lists**: Linear search is suitable for searching through unsorted lists where other more efficient algorithms (like binary search for sorted lists) cannot be applied.
  
- **Small Datasets**: It can be practical for small datasets or when a simple implementation is needed.

### Considerations:

- **Efficiency**: Linear search is simple but may not be efficient for large datasets or when frequent searches are required.
- **Performance**: For large datasets, consider sorting the list first (if feasible) and using binary search for better performance.

```python
def search(seq,target):
    for x in seq:      # direct iteration
        if x == v:
            return(True)
    return(False)
```

```python
def linear_search(seq,target)
	m = len(seq)           # Indirect iteration

	for i in range(0,m)
		if seq[i] == target
			return (i)
	return(-1)

```

### Example: Searching for a Custom Object in a List of Objects

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __eq__(self, other):
        return self.name == other.name and self.age == other.age

	def linear_search_object(arr, target):
	    for i in range(len(arr)):
	        if arr[i] == target:
	            return i
	    return -1  # Target object not found

# Example usage:
arr = [Person("Alice", 25), Person("Bob", 30), Person("Charlie", 35)]
target = Person("Bob", 30)
result_index = linear_search_object(arr, target)
if result_index != -1:
    print(f"Person {target.name} found at index {result_index}.")
else:
    print(f"Person {target.name} not found in the list.")
```
