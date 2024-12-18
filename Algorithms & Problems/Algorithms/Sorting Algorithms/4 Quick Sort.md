# Quick Sort

Divide and conquer without merging (C. Antony .R Hoare)
### Steps
If we can divide the list in such a way that everything to the right is larger than everything to the left, their will be no need to merge the two.

Suppose the median value in list A is m,
	move all the values <= m to left half of A, right half has all the values > m
	this shifting can be done in place, in time O(n)

Choose a pivot element(typically the first value in the array)
Partition A into Left Right with respect to the pivot.
Move the pivot b/w the two partitions.
recursively sort the two partitions.
One pivot and Two pointers, one moving till the middle pivot other to the end.

```
scan the list from left to right
Four segments: Pivot, Lower, Upper, Unclassified

Examine the first unclassified element
	If it is larger than the pivot, extend the upper to include this element
	If it is smaller than or equal to pivot,
***	    exchange with the first element in the upper.
		this extends the lower and shifts Upper by one possition 
	After partitioning, exchange the pivot with the last element of the lower segment,
		so pivot moves in between lower and upper

other strategies can be to to start from left side and right side, growing them towards the middle
```
### Code
```python       
def quick_sort (A, L, R):       # 2016  # one partition is in for loop

    if R - L <= 1:      # base case, at most one element
        return (A)

    yellow = L +1        # Partitioning wrt pivot A[L]
    for green in range( L+1 , R ):
        if A[green] <= A[L]:        # A[L] being the pivot
            (A[yellow], A[green]) = (A[green], A[yellow])
            yellow = yellow +1

    (A[L], A[yellow -1]) = ( A[yellow -1], A[L])   # pivot moves to middle

    quick_sort(A, L, yellow -1)      # Recursive calls
    quick_sort(A, yellow, R)
```

```python
# 2022                      # no partitions are in for loop, both incremented manually
def quicksort (L, l, r)     # to sort  L[l:r]
	if (r-l) <= 1:
		return(L)

	(pivot, lower, upper) = (L[1], l+1, l+1)   # starting of lower, upper

	for i in range (l+1, r):
		if L[i] > pivot:
			upper = upper + 1     # extend the upper segment
		else: 
			(L[i], L[lower]) = (L[lower], L[i])   # exchange L[i] with start of upper
			
			(lower, upper) = (upper+1, lower+1)   # shift both segments

	(L[1], L[lower-1]) = ( L[lower-1], L[1])      # move pivot to the middle
	lower = lower-1

	quicksort(L, l, lower)
	quicksort(L, lower+1, upper)
	return(L)
```



```python
import random

def randomize(l):
    n = len(l)
    half = n//2

    for i in range (0,half):    # mixing half the number of times as there are elements

        j = random.randrange(0,n,1)   # randrange(stop, start, step)
        k = random.randrange(0,n,1)   # Picking one one random index number in the list

        ( l[j], l[k] ) = ( l[k], l[j])  # flipping the value in those places
```

Why all GPT code is confusing!!
```python
def quick_sort(arr):
    """ Function to perform Quick Sort on the given list.  """
    
    def partition(left, right):
        """ Function to partition the array into elements less than pivot and elements
         greater than pivot. """

        pivot = arr[right]  # Choosing the last element as pivot
        i = left - 1  # Index of the smaller element

        for j in range(left, right):
            if arr[j] <= pivot:
                i += 1
                arr[i], arr[j] = arr[j], arr[i]  # Swap if element is smaller than pivot

        arr[i + 1], arr[right] = arr[right], arr[i + 1]  # Swap the pivot element to its correct position
        return i + 1

    def quick_sort_recursive(left, right):
         
        if left < right:
            pi = partition(left, right)  # Partitioning index

            quick_sort_recursive(left, pi - 1)  # Recursively sort the left sub-array
            quick_sort_recursive(pi + 1, right)  # Recursively sort the right sub-array

    quick_sort_recursive(0, len(arr) - 1)     # Call the recursive quick sort function
    return arr

# Example usage
if __name__ == "__main__":
    sample_array = [3, 6, 8, 10, 1, 2, 1]
    sorted_array = quick_sort(sample_array)
    print("Sorted array:", sorted_array)

```
### Worst case
When Pivot is either maximum or minimum, then one partitions is empty other is of size (n-1).
    T(n) = T(n-1)+n= 1+2+...+n =  O(n^2)
Already sorted array is also worst case input

Worst cases are fixed by choosing a random pivot in range(0,n) with uniform probability
then expected run time is O(n log n)
So in majority of the permutations of n elements, O(n log n) 
So quick sort is default algorithm for in-built sort functions in spreadsheets, programming languages.

### Stable sorting

Stability is important in spreadsheets, so values do not loose their place (students and marks)
the value that comes first stays first.
Often list values are tuples having sub parts
	Rows from a table, with multiple columns / attributes
	A list of students, each student entry has a roll number, name, marks,...
	
Quick sort is not very stable as swapping during partition disturbs the order.

Merge sort is stable if done carefully do not allow elements from right to overtake the elements from left favor left list when breaking ties.

