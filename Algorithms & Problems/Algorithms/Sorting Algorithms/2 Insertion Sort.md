# Insertion Sort

### Steps
1. **Start with the second element**: Assume that the first element is already sorted.
2. **Compare**: Take the current element and compare it with the elements in the sorted portion (to its left).
3. **Shift**: Shift elements in the sorted portion to the right as long as they are larger than the current element.
4. **Insert**: Insert the current element into its correct position in the sorted portion.
5. **Repeat**: Move to the next element and repeat the process until the entire list is sorted.

Kind of like moving elements from one side list to the other side of the list as a slider moves along.

First element is taken (slider at 0) (check conditions for loop, doesn't enter)
	(slider at 1) Second element compared with first in loop,
		If smaller, swapped continuously (using while loop till pos=0) 
While Loop
	each element taken, compared with one on the right, 
		if there are element to right (pos != 0),  and,  if left element is larger, enter loop.
			values are swapped.  new position will be  pos-1
				loop again to check conditions

### Code
```python
def insertion_sort(list):
	n = len(list)
	if n < 1:
		return(l)    # base case

	for slider in range(1, n):     # Slider starts from 2nd possition
		pos = slider

		while pos>0 and list[pos-1] > list[pos]:
			(list[pos-1],list[pos]) = (list[pos],list[pos-1])
			pos = pos-1
			
	return(list)
```

* Reversing > to < in while loops reverses sort order to decreasing

### Characteristics:

**Time Complexity**:
     **Average and Worst Case**: O(n²), where n is the number of elements in the list. This occurs when the list is in reverse order.
     Kind of like reverse of selection sort where the first element is not compared with any,
	last one is compared and swapped with all the previous ones, so
	T(n) = 1 + 2 + 3 + ..... + n-1 = n(n-1)/2 = (n²)/2 - n/2 
	the largest value is n² ,  Big-O is  O(n²)
    - **Best Case**: O(n), which happens when the list is already sorted.

**Space Complexity**: O(1) because it sorts the list in place with a constant amount of additional memory.

Insertion sort is intuitive and efficient for small datasets or nearly sorted data, but for large lists or data that is not already partially sorted, more advanced algorithms like quicksort or merge sort may be more efficient.

