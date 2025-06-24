# Merge Sort

### Steps
Merge sort is a classic divide-and-conquer sorting algorithm that is efficient and has a predictable time complexity.

1. **Divide**:  Split the unsorted list into two approximately equal halves.
    - If the list has more than one element, split it into two halves. This is done by finding the midpoint and creating two sub-lists: one from the start to the midpoint and the other from the midpoint to the end.

2. **Conquer**:  Recursively sort each half.
    - Recursively apply merge sort to each of the two halves until you have lists that are either empty or contain a single element (which are inherently sorted).

3. **Combine**:  Merge the two sorted halves to produce a single sorted list.
    - Merge the two sorted halves into a single sorted list. This is done by comparing the elements of the two halves and combining them in a sorted order.

Keep Dividing the array into two parts (recursively, base case, there are 0 or 1 element)
Separately sort left and right  (base case is no element in L or R)
combine the two sorted halves


Merge Sort
To sort A into B, both of length n
Base case,
    if n is 1, nothing to be done(sorted)
otherwise
    sort A[ 0 : n//2 ] into L (left)    moves 0 to (n//2)-1 elements to left list
    sort A[ n//2 : n]  into R (right)   moves (n//2) to n into right list
    merge L and R into B

Combining two sorted lists A, B into C
	while the number of elements moved is not equal to total
	Base cases
    > if A is empty, copy B into C
    > if B is empty, copy A into C
    > otherwise, compare first elements of A & B, move the smaller one of the two into C
    > repeat till A & B are empty

### Code
```python
def merge_sort(A,left,right):           # 2016 version
	(l,r) = (len(left), len(right))
	mid = (l+r)//2
			
	if r-l <= 1:
		return( A[left:right])

	if r - l > 1 
		L = return ( merge_sort( A,l,mid) )
		R = return ( merge_sort( A,mid,r) )
	return(merge(L,R))

def merge(L,R):
	(i, j, C) = (0,0,[])
	(n,m) = (len(L), len(R))

	while i+j != n+m 
		if i == n:
			C.append(R[j])
			j = j+1
	
		if j == m:
			C.append(L[i])
			i = i+1
	
		if L[i] <= R[j]:
			C.append(L[i])
			i = i+1
	
		if R[j] <= L[i]
			C.append(R[j])
			j = j+1
	return(C)
```

```python
def merge_sort(A):           # 2022 version
	n = len(A)
	if n<= 1:
		return(A)

	L = merge_sort ( A[ : n//2] )
	R = merge_sort ( A[ n//2 : ] )

	return( merge(L,R) )

def merge(L,R):
	(m,n) = (len(L),len(R))
	(C,i,j,k) = ([], 0,0,0)    # i,j are pointers for L,R  K is for C

	while k < m+n:          # Till k becomes full
		if i == m:
			C.extend(R[:j])
			k = k + (n-j)
			
		elif j == n:
			C.extend(L[:i])
			k = k + (n-i)

		elif L[i] <= R[j]:
			C.append(L[i])
			(i,k) = (i+1, k+1)

		else:
			C.append(R[j])
			(j,k) = (j+1, k+1)
	return(C)
```


```python
def merge_sort(arr):              # GPT version
    if len(arr) > 1:              # Finding the midpoint of the array
        mid = len(arr) // 2

		left_half = arr[:mid] 
		right_half = arr[mid:]
		
        merge_sort(left_half)     # Recursively sorting both halves
        merge_sort(right_half)
        
        i = j = k = 0             # Merging the sorted halves
        # Copy data to temp arrays L[] and R[]
        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1
        
        # Checking if any element was left
        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1
        
        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1

# Example usage
if __name__ == "__main__":
    arr = [38, 27, 43, 3, 9, 82, 10]
    print("Original array:", arr)
    merge_sort(arr)
    print("Sorted array:", arr)

```

### Characteristics:
- **Time Complexity**: O(n log n) for both average and worst cases, where n is the number of elements. This makes it very efficient for large datasets.
- **Space Complexity**: O(n) due to the additional space required for the temporary sub-lists used during the merge process.
- **Stability**: Merge sort is a stable sort, meaning it preserves the relative order of equal elements.

Merge sort is highly efficient and is often used in scenarios where guaranteed O(n log n) performance is required.

The merge function takes O(n), merge sort function takes O(log n)
so total is O(n log n )

No way to avoid recursion


# Variations of Merge Sort

### Union of two sorted lists (discarding duplicates)
```python
if A[i] == B[j],                                         # When both values are equal, add one value.
	Append A[i] to C, increment i & j
    if i == m or  j == n  (one of the list is empty)
		add the remaining list to C

*  (1,2,3) (2,3,4) = (1,2,3,4)
```

### Intersection of two sorted lists (finding commons)
```python
if A[i] == B[j]                       # if there are similar values
    while A[i] == B[j], increment j          # discard one value, by moving in one list
    append A[i] to C and increment i    # append one copy of that value and then move
    
if A[i] < B[j], increment i      # the value less or more are not common, move on in that list
if B[j] < A[i], increment j              

(1,2,3,4) (4,5,6) = (4)
```

### Difference of two lists (finding unique) (A-B) (B-A)

```python
# Values in A , not in B  (A-B)
if B[j] == A[i],
    discard, by incrementing i and j
if A[i] < B[j],
    append A[i] to C, increment i
if B[j] < A[i]
    discard this, increment j
Add all remaining elements from A if B is empty

(1,2,3,6) (2,4,6,8) = (1,3) 

  
Values in B , not in A  (B-A)
if B[j] == A[i],
    discard, by incrementing i and j
if B[j] < A[i]
    append to C, increment j  
if A[i] < B[j],
    discard, increment i
Add all remaining elements from B when A is empty

(1,2,3,6) (2,4,6,8) = (4,8)
```


