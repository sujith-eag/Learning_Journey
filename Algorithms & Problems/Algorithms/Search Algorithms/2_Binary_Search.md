# Binary Search
#Binarysearch
Binary search is a highly efficient algorithm for finding a target value within a sorted array or list.
It works by repeatedly dividing the search interval in half until the target value is found or the interval is empty. 
### Binary Search Algorithm:
1. **Initialization**:  Start with the entire sorted array.

2. **Midpoint Calculation**:
   - Calculate the midpoint of the current array segment (`left` to `right`).
   - `mid = (left + right) // 2`

3. **Comparison**:
   - Compare the target value with the value at the midpoint.
   - If they are equal, the target is found and return the index.
   - If the target is less than the midpoint value, search in the left subarray (`left` to `mid - 1`).
   - If the target is greater than the midpoint value, search in the right subarray (`mid + 1` to `right`).

4. **Repeat**:
   - Repeat steps 2 and 3 until the target is found or the search interval is empty (`left` > `right`).

### Considerations:
- **Sorted Input**: Binary search requires the input array to be sorted beforehand.
- **Efficiency**: Binary search has a time complexity of O(log n), where n is the number of elements in the array. This makes it significantly faster than linear search for large datasets.
- **Edge Cases**: Handle cases such as empty arrays (`arr`) or when the target value (`target`) is not present in the array.
### Example 1: Binary Search for Integer

```python
# Recursive, len(list), with left right in argument

def bisearch(seq,v,left,right):        # seq should be sorted
    mid = (left+right)//2              # Gives quotient (avoid fraction)

    if (left-right == 0):      # base case 1
        return("Not Found")
    if v == seq[mid]:   # base case 2
        return(mid)

    if v < seq[mid]:
        return( bisearch(seq,v,left,mid-1) )     # recursive
    else:
        return ( bisearch(seq,v,mid+1,right))

ss = [1,2,3,4,5,6,7,8,9,10]
print (bisearch(ss,7,0,len(ss)))
```

```python
# Recursive, Sorted list slice

def binary_search(seq,v):

	if seq == []
		return(False)

	mid = len(seq)//2
	
	if seq[mid] == v:
		return(True)

	elif seq[mid] > v:
	 return ( binary_search( seq[:mid], v ) ):
	else:
		return ( binary_search(seq[mid+1:], v ) )

```

```python
# While loop
def binary_search(arr, target):
    (left, right) = (0, len(arr)-1)
    
    while left <= right:         # The key is left <= right
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid          # Found the target, return index
            
        elif arr[mid] < target:
            left = mid + 1      # Search in the right half
        else:
            right = mid - 1     # Search in the left half
    return -1  # Target not found

# Example usage:
arr1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
target1 = 7
result_index1 = binary_search(arr1, target1)

if result_index1 != -1:
    print(f"Integer {target1} found at index {result_index1}.")
else:
    print(f"Integer {target1} not found in the list.")
```

### Example 2: Binary Search for Custom Object

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

def binary_search_object(arr, target_name):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid].name == target_name:
            return mid  # Found the target, return index
        elif arr[mid].name < target_name:
            left = mid + 1  # Search in the right half
        else:
            right = mid - 1  # Search in the left half
    return -1  # Target not found

# Example usage:
arr3 = [Person("Alice", 25), Person("Bob", 30), Person("Charlie", 35)]
target3 = "Bob"
result_index3 = binary_search_object(arr3, target3)

if result_index3 != -1:
    print(f"Person '{target3}' found at index {result_index3}.")
else:
    print(f"Person '{target3}' not found in the list.")
```