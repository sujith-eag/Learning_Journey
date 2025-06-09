

## General Concepts of Brute Force

### Define the "Brute Force" approach to problem-solving.

**Brute force is a straightforward approach to solving a problem, usually directly based on the problem statement and definitions of the concepts involved**. It can also be described by the phrase "Just do it!".

### What are the general advantages and limitations of the Brute Force method in algorithm design? 

The **principal strengths** of the brute-force approach are its **wide applicability and simplicity**. Unlike some other strategies, brute force is applicable to a very wide variety of problems. It seems to be the only general approach for which it is more difficult to point out problems it cannot tackle. Brute force algorithms are often the **easiest to apply**. 

The **principal weakness** of the brute-force approach is the **subpar efficiency of most brute-force algorithms**. It is rarely a source of clever or efficient algorithms.


### Write two key differences between the Brute Force and Divide-and-Conquer techniques of algorithm design. 

One key difference lies in their fundamental approach:
    
- **Brute force** is a straightforward method that **directly follows the problem statement and definitions**, often exploring the problem domain exhaustively or checking possibilities one by one.

- **Divide-and-conquer** solves a problem by **breaking it down into several smaller instances of the same problem**, solving each instance recursively, and then combining the solutions to the smaller instances to obtain a solution to the original problem.

Another difference is in how they handle subproblems:

- **Brute force** typically tackles the problem directly or by systematically generating and checking candidates.

- **Divide-and-conquer** solves smaller instances of the _same problem_. These subproblems are usually independent.

### When might a Brute Force approach be considered a practical or reasonable choice for solving a problem? 

A brute-force algorithm can be a practical or reasonable choice in several situations:
    
- When the **expense of designing a more efficient algorithm may be unjustifiable** if only a few instances of a problem need to be solved and a brute-force algorithm can solve those instances with acceptable speed.

- For some important problems like sorting, searching, matrix multiplication, and string matching, the brute-force approach yields **reasonable algorithms of at least some practical value with no limitation on instance size**.

- Even if too inefficient in general, a brute-force algorithm can still be **useful for solving small-size instances** of a problem.

- A brute-force algorithm can serve an important theoretical or educational purpose as a **yardstick with which to judge more efficient alternatives** for solving a problem.

- Its **wide applicability and simplicity** also make it a default approach when more sophisticated methods are not immediately obvious or necessary.

- A first application of the brute-force approach often results in an algorithm that can be **improved with a modest amount of effort**.


## Selection Sort

## Describe the Selection Sort algorithm. 

Selection sort is a **brute-force approach** to the sorting problem. It works by repeatedly finding the **smallest element** from the unsorted portion of the list and **exchanging it with the element at the current position**. 

Specifically, the algorithm starts by scanning the entire list to find its smallest element and swaps it with the first element. Then, it scans the list starting from the second element to find the smallest among the remaining elements and swaps it with the second element. This process continues, where on the _i_th pass (from 0 to _n_ - 2), the algorithm searches for the smallest item among the last _n_ - _i_ elements and swaps it with the element at position _i_. After _n_ - 1 passes, the list is sorted.

### Write a clear algorithm or pseudocode for Selection Sort. 

```
ALGORITHM SelectionSort(A[0..n − 1])
//Sorts a given array by selection sort
//Input: An array A[0..n − 1] of orderable elements
//Output: Array A[0..n − 1] sorted in nondecreasing order
for i ← 0 to n − 2 do
	min ← i
	for j ← i + 1 to n − 1 do
		if A[j ] < A[min]
			min ← j
	swap A[i] and A[min]
```


### Analyze the time complexity of the Selection Sort algorithm. 

The analysis of selection sort is straightforward.

- The input size is the number of elements, _n_.
- The basic operation is the **key comparison** `A[j] < A[min]`.
- The number of times this basic operation is executed depends _only_ on the array size _n_. Thus, there is no need to distinguish between worst-case, average-case, and best-case efficiency for the number of comparisons.

- The number of comparisons is given by the sum: _C(n) =_ ∑_i=0__n-2_ ∑_j=i+1__n-1_ 1
- This sum evaluates to ∑_i=0__n-2_ (_n_ - 1 - _i_), which is the sum of decreasing integers from _n_ - 1 down to 1.
- The result of this sum is **(_n_ - 1)_n_ / 2**.
- Therefore, selection sort is a **Θ(n2)** algorithm for key comparisons on all inputs.

- Note that the number of key swaps is _n_ - 1, which is in **Θ(n)**. This property positively distinguishes it from many other sorting algorithms.


### Trace the execution of the Selection Sort algorithm on the following lists of numbers/characters:

- `` (n=7)

Initial list: ``

- i = 0: Find minimum in ``. Minimum is 15 at index 6. Swap `A` and `A`. State:``
	
- i = 1: Find minimum in ``. Minimum is 21 at index 4 (of original array, index 3 of sublist). Swap `A` and `A`. State:``
	
- i = 2: Find minimum in ``. Minimum is 34 at index 5 (of original array, index 3 of sublist). Swap `A` and `A`. State:``
	
- i = 3: Find minimum in ``. Minimum is 43 at index 4 (of original array, index 1 of sublist). Swap `A` and `A`. State:``
	
- i = 4: Find minimum in ``. Minimum is 66 at index 5 (of original array, index 1 of sublist). Swap `A` and `A`. State:``
	
- i = 5: Find minimum in ``. Minimum is 81 at index 6 (of original array, index 1 of sublist). Swap `A` and `A`. State:``
	
- i = 6: Loop finishes as i goes up to n-2 (which is 5).
	

Sorted list: ``

- `[S, E, Q, U, E, N, T, I, A, L]` (in alphabetical order) (n=10)

Initial list: `[S, E, Q, U, E, N, T, I, A, L]`

- i = 0: Min is 'A' at index 8. Swap A and A. State: `[A, E, Q, U, E, N, T, I, S, L]`
	
- i = 1: Min is 'E' at index 1. Swap A and A. State: `[A, E, Q, U, E, N, T, I, S, L]` (No change)
	
- i = 2: Min in `[Q, U, E, N, T, I, S, L]` is 'E' at index 4 (original index). Swap A and A. State: `[A, E, E, U, Q, N, T, I, S, L]`
	
- i = 3: Min in `[U, Q, N, T, I, S, L]` is 'I' at index 7 (original index). Swap A and A. State: `[A, E, E, I, Q, N, T, U, S, L]`
	
- i = 4: Min in `[Q, N, T, U, S, L]` is 'L' at index 9 (original index). Swap A and A. State: `[A, E, E, I, L, N, T, U, S, Q]`
	
- i = 5: Min in `[N, T, U, S, Q]` is 'N' at index 5 (original index). Swap A and A. State: `[A, E, E, I, L, N, T, U, S, Q]` (No change)
	
- i = 6: Min in `[T, U, S, Q]` is 'Q' at index 9 (original index). Swap A and A. State: `[A, E, E, I, L, N, Q, U, S, T]`
	
- i = 7: Min in `[U, S, T]` is 'S' at index 8 (original index). Swap A and A. State: `[A, E, E, I, L, N, Q, S, U, T]`
	
- i = 8: Min in `[U, T]` is 'T' at index 9 (original index). Swap A and A. State: `[A, E, E, I, L, N, Q, S, T, U]`
	
- i = 9: Loop finishes as i goes up to n-2 (which is 8).
	

Sorted list: `[A, E, E, I, L, N, Q, S, T, U]`

### Is Selection Sort a stable sorting algorithm? Explain your answer.

**No, selection sort is not stable**. A sorting algorithm is stable if it preserves the relative order of any two equal elements in its input. 

If an input list contains two equal elements in positions _i_ and _j_ where _i_ < _j_, then in the sorted list they must be in positions _i'_ and _j'_ respectively, such that _i'_ < _j'_. Selection sort can violate this property because it **exchanges elements that are not necessarily adjacent** to each other. 

In the process of swapping the minimum element found in the unsorted portion with the element at the current position (_A[i]_), the algorithm can reverse the original ordering of equal elements. 

Consider the list `[A1, B, A2]`, where A1 and A2 are equal, and A1 appears before A2. The minimum is A1. It's already in the first position. The algorithm proceeds. The minimum in `[B, A2]` is A2. It gets swapped with B. The resulting list is `[A1, A2, B]`. The relative order of A1 and A2 is preserved here. Let's try `[B, A1, A2]`. The minimum is A1. It's swapped with B. The list becomes `[A1, B, A2]`. Again, the order is preserved. A better example to show instability is `[A2, B, A1]`. The minimum is A1. It's swapped with A2. The list becomes `[A1, B, A2]`. The original order of A1 (index 2) before A2 (index 0) is reversed to A1 (index 0) before A2 (index 2). Thus, selection sort is not stable.


## Brute_Force String Matching

### Explain the Brute-Force String Matching algorithm. 

The Brute-Force String Matching problem involves finding a substring within a larger string (called the text) that matches a given string (called the pattern). 

More precisely, the goal is to find the index of the leftmost character in the text where the first matching substring begins. 

Brute-force, approach to solving this problem involves aligning the pattern against the first _m_ characters of the text (where _m_ is the length of the pattern) and then comparing the corresponding pairs of characters from left to right. If all _m_ pairs match, the algorithm can stop, indicating a successful search. If a mismatching pair is encountered, the pattern is shifted one position to the right, and character comparisons resume, starting again with the first character of the pattern and its new counterpart in the text. This process continues, with the algorithm checking alignments until the pattern extends beyond the text. The last possible position in the text where a matching substring can start is _n_ - _m_ (assuming text positions are indexed from 0 to _n_ - 1, where _n_ is the text length).
    

### Write an algorithm or pseudocode for the Brute-Force String Matching technique. 

Here is the pseudocode for the Brute-Force String Matching algorithm:

```
ALGORITHM BruteForceStringMatch(T[0..n − 1], P[0..m − 1])
//Implements brute-force string matching
//Input: An array T[0..n − 1] of n characters representing a text and
// an array P[0..m − 1] of m characters representing a pattern
//Output: The index of the first character in the text that starts a
// matching substring or −1 if the search is unsuccessful
for i ← 0 to n − m do
	j ← 0
	while j < m and P[j] = T[i + j] do
		j ← j + 1
	if j = m return i
return −1
```

### Analyze the time complexity of the Brute-Force String Matching algorithm. 

The analysis of the brute-force string-matching algorithm focuses on the number of character comparisons. The input consists of a text of length _n_ and a pattern of length _m_ (where _m_ ≤ _n_). The basic operation is the comparison `P[j] = T[i + j]`.

In the **worst case**, the algorithm might have to make all _m_ comparisons before shifting the pattern. This can happen for each of the _n_ - _m_ + 1 possible alignments of the pattern within the text. An example of a worst-case input is searching for a pattern like `10...0` (a 1 followed by m-1 zeros) in a text of n zeros, or more generally, patterns and texts where mismatches always occur on the last character of the pattern. In this scenario, for each of the _n - m + 1_ alignments, the algorithm performs _m_ comparisons (m-1 successful, 1 unsuccessful) before shifting. Thus, the total number of character comparisons in the worst case is **m(n - m + 1)**, which puts the algorithm in the **O(nm)** efficiency class.

For searching in a **typical natural language text**, however, most shifts are expected to occur after very few comparisons. Therefore, the **average-case efficiency** is considerably better than the worst-case efficiency. For searching in random texts, the average-case efficiency has been shown to be **linear, i.e., Θ(n)**.

### Trace the Brute-Force String Matching algorithm for the following scenarios:

- Pattern: `"COMPUTER"`, Text: `"MASTER OF COMPUTER APPLICATIONS"`
	
	- Text (T): `MASTER OF COMPUTER APPLICATIONS` (n=29, indexing from 0 to 28)
	- Pattern (P): `COMPUTER` (m=8, indexing from 0 to 7)
	- The loop for `i` runs from 0 to n - m = 29 - 8 = 21.
	
	1. **i = 0:** Align P at index 0 of T. Compare `T` ('M') and `P` ('C'). Mismatch. Shift P.
	2. **i = 1:** Align P at index 1 of T. Compare `T` ('A') and `P` ('C'). Mismatch. Shift P.
	3. **i = 2:** Align P at index 2 of T. Compare `T` ('S') and `P` ('C'). Mismatch. Shift P.
	4. **i = 3:** Align P at index 3 of T. Compare `T` ('T') and `P` ('C'). Mismatch. Shift P.
	5. **i = 4:** Align P at index 4 of T. Compare `T` ('E') and `P` ('C'). Mismatch. Shift P.
	6. **i = 5:** Align P at index 5 of T. Compare `T` ('R') and `P` ('C'). Mismatch. Shift P.
	7. **i = 6:** Align P at index 6 of T. Compare `T` (' ') and `P` ('C'). Mismatch. Shift P.
	8. **i = 7:** Align P at index 7 of T. Compare `T` ('O') and `P` ('C'). Mismatch. Shift P.
	9. **i = 8:** Align P at index 8 of T. Compare `T` ('F') and `P` ('C'). Mismatch. Shift P.
	10. **i = 9:** Align P at index 9 of T. Compare `T` (' ') and `P` ('C'). Mismatch. Shift P.
	11. **i = 10:** Align P at index 10 of T. Compare `T` ('C') and `P` ('C'). Match. Compare `T` ('O') and `P` ('O'). Match. Compare `T` ('M') and `P` ('M'). Match. Compare `T` ('P') and `P` ('P'). Match. Compare `T` ('U') and `P` ('U'). Match. Compare `T` ('T') and `P` ('T'). Match. Compare `T` ('E') and `P` ('E'). Match. Compare `T` ('R') and `P` ('R'). Match. All characters matched (`j` becomes 8, which equals `m`). Return `i`. Found match at index 10.
- Pattern: `"EE"`, Text: `"ENGINEERING COLLEGE"`
	
	- Text (T): `ENGINEERING COLLEGE` (n=20, indexing from 0 to 19)
	- Pattern (P): `EE` (m=2, indexing from 0 to 1)
	- The loop for `i` runs from 0 to n - m = 20 - 2 = 18.
	
	1. **i = 0:** Align P at index 0 of T. Compare `T` ('E') and `P` ('E'). Match. Compare `T` ('N') and `P` ('E'). Mismatch. Shift P.
	2. **i = 1:** Align P at index 1 of T. Compare `T` ('N') and `P` ('E'). Mismatch. Shift P.
	3. **i = 2:** Align P at index 2 of T. Compare `T` ('G') and `P` ('E'). Mismatch. Shift P.
	4. **i = 3:** Align P at index 3 of T. Compare `T` ('I') and `P` ('E'). Mismatch. Shift P.
	5. **i = 4:** Align P at index 4 of T. Compare `T` ('N') and `P` ('E'). Mismatch. Shift P.
	6. **i = 5:** Align P at index 5 of T. Compare `T` ('E') and `P` ('E'). Match. Compare `T` ('E') and `P` ('E'). Match. All characters matched (`j` becomes 2, which equals `m`). Return `i`. Found match at index 5.



## Exhaustive Search

### Define "Exhaustive Search" as an approach to problem-solving. (How does it relate to Brute force strategy) 

Exhaustive search is simply a brute-force approach to combinatorial problems. It involves generating each and every element of the problem domain, selecting those of them that satisfy all the constraints, and then finding a desired element (e.g., the one that optimizes some objective function). 

Brute force itself is defined as a straightforward approach to solving a problem, usually directly based on the problem statement and definitions of the concepts involved. Thus, exhaustive search is a specific application of the general brute-force strategy tailored for problems that require searching through a large number of combinatorial objects.

### Demonstrate the use of Exhaustive Search for the Traveling Salesperson Problem (TSP) with a suitable example. 

The Traveling Salesperson Problem (TSP) asks to find the shortest tour through a given set of _n_ cities that visits each city exactly once before returning to the starting city. It can be modeled by a weighted graph where vertices are cities and edge weights are distances. 

The problem becomes finding the shortest Hamiltonian circuit in the graph. The exhaustive-search approach for TSP involves generating all permutations of the cities, calculating the total tour length for each permutation, and then finding the shortest tour among them. 

As an example, consider the small instance with four cities (a, b, c, d) and given edge weights. We can fix city 'a' as the starting point without loss of generality. We then generate all permutations of the remaining _n_-1 cities (b, c, d). For n=4, there are (4-1)! = 3! = 6 permutations of cities b, c, d. These permutations define the possible tours starting and ending at 'a':

- a -> b -> c -> d -> a. Tour length: 2 + 8 + 1 + 7 = 18
- a -> b -> d -> c -> a. Tour length: 2 + 3 + 1 + 5 = 11
- a -> c -> b -> d -> a. Tour length: 5 + 8 + 3 + 7 = 23
- a -> c -> d -> b -> a. Tour length: 5 + 1 + 3 + 2 = 11
- a -> d -> b -> c -> a. Tour length: 7 + 3 + 8 + 5 = 23
- a -> d -> c -> b -> a. Tour length: 7 + 1 + 8 + 2 = 18

By examining these tours and their lengths, the exhaustive search finds that the shortest tours have a length of 11. Note that some tours are just the reverse direction of others (e.g., a-b-d-c-a and a-c-d-b-a both have length 11).
    

### Solve the following 0/1 Knapsack problem using Exhaustive Search, given a capacity W=10:
    
| Item | Weight | Value |
|------|--------|-------|
| 1    | 7      | $42   |
| 2    | 3      | $12   |
| 3    | 4      | $40   |
| 4    | 5      | $25   |

Knapsack capacity W = 10. Items with weights w1=7, w2=3, w3=4, w4=5 and values v1=$42, v2=$12, v3=$40, v4=$25. 

The exhaustive-search approach to the 0/1 Knapsack problem involves generating all possible subsets of the given items, checking if the total weight of each subset is within the knapsack's capacity (feasible subsets), and then finding the feasible subset with the maximum total value. For n=4 items, there are 2^4 = 16 possible subsets:
    
- ∅: Total weight 0, Total value $0. Feasible.
- {1}: Total weight 7, Total value $42. Feasible.
- {2}: Total weight 3, Total value $12. Feasible.
- {3}: Total weight 4, Total value $40. Feasible.
- {4}: Total weight 5, Total value $25. Feasible.
- {1, 2}: Total weight 7 + 3 = 10, Total value $42 + $12 = $54. Feasible.
- {1, 3}: Total weight 7 + 4 = 11, Total value $42 + $40 = $82. Not feasible (weight > 10).
- {1, 4}: Total weight 7 + 5 = 12, Total value $42 + $25 = $67. Not feasible (weight > 10).
- {2, 3}: Total weight 3 + 4 = 7, Total value $12 + $40 = $52. Feasible.
- {2, 4}: Total weight 3 + 5 = 8, Total value $12 + $25 = $37. Feasible.
- {3, 4}: Total weight 4 + 5 = 9, Total value $40 + $25 = $65. Feasible.
- {1, 2, 3}: Total weight 7 + 3 + 4 = 14, Total value $42 + $12 + $40 = $94. Not feasible (weight > 10).
- {1, 2, 4}: Total weight 7 + 3 + 5 = 15, Total value $42 + $12 + $25 = $79. Not feasible (weight > 10).
- {1, 3, 4}: Total weight 7 + 4 + 5 = 16, Total value $42 + $40 + $25 = $107. Not feasible (weight > 10).
- {2, 3, 4}: Total weight 3 + 4 + 5 = 12, Total value $12 + $40 + $25 = $77. Not feasible (weight > 10).
- {1, 2, 3, 4}: Total weight 7 + 3 + 4 + 5 = 19, Total value $42 + $12 + $40 + $25 = $119. Not feasible (weight > 10).
    
Comparing the values of the feasible subsets ($0, $42, $12, $40, $25, $54, $52, $37, $65), the maximum value is $65. The subset corresponding to this value is **{item 3, item 4}**. This is the optimal solution by exhaustive search for this instance.

### Discuss the primary limitations of using Exhaustive Search for solving complex combinatorial problems. 

The primary limitation of exhaustive search is its **extreme inefficiency on most inputs**. This difficulty stems from the fact that the **number of combinatorial objects (like permutations or subsets) typically grows extremely fast with a problem’s size**, often exponentially or faster. 

For problems like the Traveling Salesperson Problem, the number of permutations grows as n! (factorial of the number of cities). 

For the Knapsack problem, the number of subsets is 2^n (2 raised to the power of the number of items). This rapid growth means that even for moderate-sized instances, the number of objects to generate and check becomes astronomically large, reaching "unimaginable magnitudes". 

Consequently, **exhaustive search is impractical for all but very small instances of the problems it can be applied to**. For many such problems, there are no known algorithms that can solve them exactly in an acceptable amount of time, leading to the belief by most computer scientists that such efficient algorithms do not exist. Problems like TSP and the 0/1 Knapsack are classic examples of these computationally hard problems, known as NP-hard problems.

