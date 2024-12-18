# Selection Sort

### Steps:
**Initial Step**:  Begin with the first element of the list. Assume this element is the minimum.
**Find the Minimum**: Traverse the unsorted portion of the list to find the smallest element.
**Swap**: Swap the smallest found element with the first unsorted element.
**Move the Boundary**:  Move the boundary between the sorted and unsorted parts one position to the right.
**Repeat**: Repeat the process for the remaining unsorted portion of the list until the entire list is sorted.

1. Consider first element (zero index) as lowest, compare it to value in (next index).
2. If it is lesser then consider that index as min index, 
3. Go through all the values, by the end of a run index of lowest number will be found.
4. Swap places with first.
5. Start again in second value (skipping the first)
6. The second element is selected and again compared with all other values to pick smallest, replaced with value in second place and so on till last element, 

* 1st (for loop) to iterate through portions of list(slice) and swap positions.
	* 2nd (for loop) to find the position with with minimum value.
	* pass it to previous (for loop) and swap positions.

* 1st (for loop) will start again with next place of list, skipping the changed value

### Code
```python
def selection_sort(list):
	n = len(list)
	if n<1:
		return(list)      # Base case, empty list
		
	for first in range(0, n):    # for scanning dif slices of list
		min_pos = first
		
			for i in range(first+1, n):  # for finding min_pos
				if list[min_pos] > list[i]:
					min_pos = i
					
		(list[first], list[min_pos]) = (list[min_pos], list[first]) # swapping values
	return(list)
```

```python   
#One more similar
def selection_sort(arr):
    n = len(arr)

    for i in range(n):
        min_index = i     # Assume the current index is the minimum
        
        # Find the index of the smallest element in the remaining unsorted portion
        for j in range(i+1, n):
            if arr[j] < arr[min_index]:
                min_index = j
        
        # Swap the found minimum element with the element at the current index
        arr[i], arr[min_index] = arr[min_index], arr[i]

# Example usage
if __name__ == "__main__":
    arr = [64, 25, 12, 22, 11]
    print("Original array:", arr)
    selection_sort(arr)
    print("Sorted array:", arr)
```

### Characteristics:
- **Time Complexity**: O(n²) in both average and worst cases, where n is the number of elements. This is due to the nested loops—one for finding the minimum element and another for swapping.
- The number of comparisons keeps on decreasing from n till 1 in worst case (if list is reverse sorted or sorted)
	Big-O is, O(n^2)
	T(n)= n + (n-1) + (n-2) +...+ 1 = n(n+1)/2 = (n^2)/2 + n/2
	The maximum value is n^2	
	
* All cases are Worst case. Even when a list is already sorted, Selection sort will scan through the list of (n elements) and compare it to all the elements (n times), worst case of n^2.

- **Space Complexity**: O(1) since it sorts the list in place with a constant amount of additional memory.
- **Stability**: Selection sort is not a stable sort, meaning that it does not necessarily preserve the relative order of equal elements.
