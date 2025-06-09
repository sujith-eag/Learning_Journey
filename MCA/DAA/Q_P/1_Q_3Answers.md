
## Mathematical Analysis of Non-Recursive Algorithms


### Outline the general plan or steps for analyzing the time efficiency of non-recursive algorithms. 

The general plan for analyzing the time efficiency of non-recursive algorithms involves several steps:

- **Decide on a parameter (or parameters) indicating an input’s size.** This parameter, often denoted as _n_, represents the scale of the input (e.g., the number of elements in a list, the order of a matrix).

- **Identify the algorithm’s basic operation.** This is typically the operation that contributes the most to the total running time, often found in the innermost loop of the algorithm. Examples include comparisons in sorting/searching algorithms or arithmetic operations in mathematical algorithms.

- **Check whether the number of times the basic operation is executed depends only on the size of an input.** If the count can vary for inputs of the same size, you need to investigate the worst-case, average-case, and, if necessary, best-case efficiencies separately.

- **Set up a sum expressing the number of times the algorithm’s basic operation is executed.** This summation represents the total count of the basic operation.

- **Using standard formulas and rules of sum manipulation, either find a closed-form formula for the count or, at the very least, establish its order of growth.** This step involves mathematical analysis of the sum to express the operation count as a function of the input size parameter _n_, often resulting in an asymptotic notation like Θ(_g_(_n_)).


### Develop an algorithm for the "element uniqueness problem" (checking if all elements in a given array are distinct) and derive its time complexity.

```
ALGORITHM UniqueElements(A[0..n − 1])
//Determines whether all the elements in a given array are distinct

//Input: An array A[0..n − 1]
//Output: Returns “true” if all the elements in A are distinct
// and “false” otherwise

for i ← 0 to n − 2 do
	for j ← i + 1 to n − 1 do
		if A[i] = A[j ]
			return false
return true
```

To derive its time complexity:

- **Input size:** The natural measure is the number of elements in the array, _n_.

- **Basic operation:** The most frequently executed operation is the comparison `A[i] = A[j]` in the innermost loop.

- **Does count depend on input specifics?** Yes, the number of comparisons depends on whether there are duplicate elements and their positions. We analyze the worst case.

- **Set up a sum:** In the worst case, the algorithm compares every distinct pair of elements. This happens if all elements are distinct or if the only duplicate pair is the very last one checked. The number of comparisons is given by the sum: `Cworst(n) = ∑_{i=0}^{n-2} ∑_{j=i+1}^{n-1} 1`

- **Solve the sum:** The inner sum `∑_{j=i+1}^{n-1} 1` is the number of terms from `i+1` to `n-1`, which is `(n-1) - (i+1) + 1 = n - 1 - i`. So the sum becomes `∑_{i=0}^{n-2} (n - 1 - i)`. This sum represents the series `(n-1) + (n-2) + ... + 1`. Using the formula for the sum of the first _k_ positive integers `k(k+1)/2`, where _k_ = `n-1`, we get `(n-1)n / 2`.

- **Order of growth:** `Cworst(n) = n(n-1)/2 = (n² - n)/2`. The highest order term is _n²_, so the time complexity is in **Θ(n²)**.


### Consider the following algorithm:

```
ALGORITHM Sum(n)
// Input: A non-negative integer n
Sum ← 0
For i ← 1 to n do
	Sum ← Sum + i
Return Sum
```

a) **What task does this algorithm perform?** This algorithm computes the **sum of the first _n_ positive integers** (1 + 2 + ... + _n_).

b) **Identify the basic operation.** The loop iterates from 1 to _n_. The operation performed inside the loop that contributes most to the running time is the **addition** `Sum ← Sum + i`.

c) **Determine how many times the basic operation is executed as a function of `n`.** The `for` loop iterates _n_ times (for i from 1 to _n_). The addition operation is executed exactly once in each iteration. Therefore, the basic operation (addition) is executed **n** times as a function of _n_. 

We can express this as `C(n) = n`. This count is the same for any input size _n_, so we don't need separate worst, average, or best cases. The time complexity is in **Θ(n)**.


### Develop an algorithm for multiplying two `n x n` matrices and analyze its time complexity. 

Multiplying two _n_ x _n_ matrices, A and B, to produce a matrix C = AB:

```
ALGORITHM MatrixMultiplication(A[0..n − 1, 0..n − 1], B[0..n − 1, 0..n − 1])
//Multiplies two square matrices of order n by the definition-based algorithm
//Input: Two n × n matrices A and B
//Output: Matrix C = AB
for i ← 0 to n − 1 do
	for j ← 0 to n − 1 do
		C[i, j ] ← 0.0
		for k ← 0 to n − 1 do
			C[i, j ] ← C[i, j ] + A[i, k] ∗ B[k, j ]
return C
```

To analyze its time complexity:

- **Input size:** The natural measure is the order of the matrices, _n_.
- **Basic operation:** There are two arithmetic operations in the innermost loop: multiplication (`*`) and addition (`+`). The sources state that multiplication is traditionally considered the basic operation, but since both are executed once per innermost loop iteration, counting one counts the other. We consider **multiplication** as the basic operation.
- **Does count depend on input specifics?** No, the number of multiplications is the same for all _n_ x _n_ matrices.
- **Set up a sum:** The algorithm has three nested loops. The outermost loop runs _n_ times (for `i` from 0 to `n-1`). The middle loop runs _n_ times for each iteration of the outer loop (for `j` from 0 to `n-1`). The innermost loop runs _n_ times for each iteration of the outer two loops (for `k` from 0 to `n-1`). The multiplication `A[i, k] * B[k, j]` is performed inside the innermost loop. The total number of multiplications, M(_n_), is given by the sum: `M(n) = ∑_{i=0}^{n-1} ∑_{j=0}^{n-1} ∑_{k=0}^{n-1} 1`
- **Solve the sum:** Evaluating the sum from the inside out: `∑_{k=0}^{n-1} 1 = n` `∑_{j=0}^{n-1} n = n * n = n²` `∑_{i=0}^{n-1} n² = n * n² = n³`
- **Order of growth:** The total number of multiplications is `M(n) = n³`. The time complexity is in **Θ(n³)**. The sources note that the number of additions is also _n³_, and the overall time efficiency is dominated by the cubic term, `(cm + ca)n³`, where cm and ca are the times for multiplication and addition respectively.

### Write a non-recursive algorithm to compute the factorial of a given non-negative integer `n` and analyze its time efficiency. 

```
ALGORITHM NonRecursiveFactorial(n)
// Computes n! non-recursively
// Input: A non-negative integer n
// Output: The value of n!
if n < 0 return error // Factorial is defined for non-negative integers
if n = 0 return 1
factorial ← 1
for i ← 1 to n do
	factorial ← factorial * i
return factorial
```

To analyze its time efficiency:

- **Input size:** The natural measure is the integer _n_ itself.
- **Basic operation:** The loop iterates from 1 to _n_. The operation inside the loop that is performed repeatedly is the **multiplication** `factorial ← factorial * i`.
- **Does count depend on input specifics?** No, for a given _n_, the loop always runs the same number of times.
- **Set up a sum:** The multiplication operation is executed once for each value of `i` from 1 to _n_. If we count the multiplications in the loop: `∑_{i=1}^{n} 1`.
- **Solve the sum:** The sum is 1 added _n_ times, which equals _n_. For the base case `n=0`, there are 0 multiplications in the loop. The function `C(n) = n` for `n > 0` and `C(0) = 0` correctly represents the number of multiplications.
- **Order of growth:** The number of multiplications is _n_. The time complexity is in **Θ(n)**. The sources mention that the iterative computation of factorial is more efficient than the discussed recursive one because it avoids the overhead of the recursion stack.

### Design a non-recursive algorithm to compute the sum of the squares of the first ‘n’ natural numbers (i.e., 1² + 2² + ... + n²). Analyze its time complexity.

```
ALGORITHM SumOfSquares(n)
// Computes the sum of the squares of the first n natural numbers
// Input: A non-negative integer n
// Output: The value of 1^2 + 2^2 + ... + n^2
if n < 0 return error
if n = 0 return 0
Sum ← 0
for i ← 1 to n do
	term ← i * i // Compute i^2
	Sum ← Sum + term // Add to the total sum
return Sum
```

To analyze its time efficiency:

- **Input size:** The natural measure is the integer _n_.
- **Basic operation:** The loop iterates _n_ times. Inside the loop, we have a multiplication (`i * i`) and an addition (`Sum ← Sum + term`). Since both are executed once per iteration, we can pick one, traditionally the **multiplication** as it can be more time-consuming. Or, as the sources mention, if executed equally often, choosing either is fine. Let's count multiplications.
- **Does count depend on input specifics?** No, the count is the same for a given _n_.
- **Set up a sum:** The multiplication `i * i` is executed once for each value of `i` from 1 to _n_. The sum is `∑_{i=1}^{n} 1`.
- **Solve the sum:** The sum is 1 added _n_ times, which is _n_.
- **Order of growth:** The number of multiplications is _n_. The time complexity is in **Θ(n)**.


### Analyze the time complexity of an algorithm that finds the maximum element in an array of `n` numbers. 

```
ALGORITHM MaxElement(A[0..n − 1])
//Determines the value of the largest element in a given array
//Input: An array A[0..n − 1] of real numbers
//Output: The value of the largest element in A
maxval ← A
for i ← 1 to n − 1 do
	if A[i] > maxval
		maxval ← A[i]
return maxval
```

To analyze its time complexity:

- **Input size:** The number of elements in the array, _n_.
- **Basic operation:** The operation executed most often is the **comparison** `A[i] > maxval` within the loop.
- **Does count depend on input specifics?** No, the number of comparisons is the same for all arrays of size _n_.
- **Set up a sum:** The comparison is executed once for each iteration of the `for` loop, which runs for `i` from 1 to `n-1`. The number of comparisons is `C(n) = ∑_{i=1}^{n-1} 1`.
- **Solve the sum:** The sum is 1 added `n-1` times, resulting in `n-1`.
- **Order of growth:** The number of comparisons is `C(n) = n-1`. The time complexity is in **Θ(n)**.


### How do you analyze algorithms with nested loops? Provide an example. 

Algorithms with nested loops are analyzed by following the general plan for non-recursive algorithms. The key step is identifying the basic operation, which is typically located in the **innermost loop**. You then set up a sum representing the number of times this basic operation is executed. 

For nested loops, this sum will involve multiple summation signs, one for each loop level. You evaluate the sum by starting from the innermost loop and working outwards.

**Example:** The **element uniqueness problem** algorithm involves two nested loops:

```
for i ← 0 to n − 2 do
	for j ← i + 1 to n − 1 do
		if A[i] = A[j ] // Basic operation
			return false
```

The basic operation is the comparison `A[i] = A[j]`. The number of comparisons is given by the sum `∑_{i=0}^{n-2} ∑_{j=i+1}^{n-1} 1`. The outer loop variable `i` goes from 0 to `n-2`. The inner loop variable `j` goes from `i+1` to `n-1`. Evaluating the inner sum `∑_{j=i+1}^{n-1} 1` yields `(n-1) - (i+1) + 1 = n - 1 - i`. The outer sum then becomes `∑_{i=0}^{n-2} (n - 1 - i)`. This sum is equivalent to `(n-1) + (n-2) + ... + 1`, which sums to `n(n-1)/2`. Therefore, the time complexity of this algorithm is **Θ(n²)**, typically characterizing the efficiency of algorithms with two embedded loops.

Another example is **matrix multiplication**, which has three nested loops. The basic operation (multiplication) is in the innermost loop. The number of operations is given by the sum `∑_{i=0}^{n-1} ∑_{j=0}^{n-1} ∑_{k=0}^{n-1} 1`. Evaluating this triple sum results in _n³_, which is typical for algorithms with three embedded loops.