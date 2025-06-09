
## Mathematical Analysis of Recursive Algorithms


### What is a recurrence relation? How is it used to describe the efficiency of recursive algorithms?

- A **recurrence relation** is an equation that defines a sequence not explicitly as a function of _n_, but implicitly as a function of its value at another point, such as _n-1_ or _n/2_. These equations play an important role in the analysis of algorithms and in areas of applied mathematics.
- Recurrence relations are the **main tool for analyzing the time efficiency of a recursive algorithm**. When analyzing a recursive algorithm, the number of times the algorithm's basic operation is executed is expressed using a recurrence relation, along with an appropriate initial condition. Solving this recurrence relation allows us to find an explicit formula for the number of basic operations in terms of the input size _n_. Ascertaining the order of growth of this solution provides the algorithm's efficiency class.

### Describe the general plan or steps for analyzing the time efficiency of recursive algorithms. 

The general plan for analyzing the time efficiency of recursive algorithms involves the following steps:

1. **Decide on a parameter** (or parameters) indicating an input’s size.
2. **Identify the algorithm’s basic operation**.
3. **Check whether the number of times the basic operation is executed can vary** on different inputs of the same size; if it can, the worst-case, average-case, and best-case efficiencies must be investigated separately.
4. **Set up a recurrence relation, with an appropriate initial condition**, for the number of times the basic operation is executed.
5. **Solve the recurrence or, at least, ascertain the order of growth of its solution**.

### Explain the recursive algorithm for the Towers of Hanoi problem.

- The Towers of Hanoi is a puzzle with _n_ disks of different sizes and three pegs. Initially, all the disks are on the first peg, ordered by size with the largest at the bottom and the smallest on top. The goal is to move all the disks to the third peg, using the second peg as an auxiliary. The rules are that only one disk can be moved at a time, and a larger disk can never be placed on top of a smaller one.
- The puzzle has an elegant recursive solution. To move _n > 1_ disks from a source peg to a destination peg (using an auxiliary peg):
	1. Recursively move the top _n-1_ disks from the source peg to the auxiliary peg (using the destination peg as the temporary auxiliary).
	2. Move the largest disk directly from the source peg to the destination peg.
	3. Recursively move the _n-1_ disks from the auxiliary peg to the destination peg (using the source peg as the temporary auxiliary).
- The base case for the recursion is when _n = 1_, where the single disk is moved directly from the source to the destination peg.

### Set up the recurrence relation for the number of moves in the Towers of Hanoi problem and solve it to determine the algorithm's time efficiency.

- For the Towers of Hanoi problem, the number of disks _n_ is the input size, and moving a single disk is the basic operation. Let _M(n)_ be the number of moves.
- Based on the recursive solution for _n > 1_ disks, moving _n_ disks requires:
	1. _M(n-1)_ moves to transfer the top _n-1_ disks to the auxiliary peg.
	2. 1 move to transfer the largest disk to the destination peg.
	3. _M(n-1)_ moves to transfer the _n-1_ disks from the auxiliary peg to the destination peg.
- This leads to the recurrence relation: **M(n) = M(n - 1) + 1 + M(n - 1) for n > 1**.
- Simplifying, we get **M(n) = 2M(n - 1) + 1 for n > 1**.
- The initial condition is for _n = 1_, where only one move is needed: **M(1) = 1**.
- We can solve this recurrence using the method of backward substitutions:
	- M(n) = 2M(n-1) + 1
	- Substitute M(n-1) = 2M(n-2) + 1: M(n) = 2[2M(n-2) + 1] + 1 = 2²M(n-2) + 2 + 1
	- Substitute M(n-2) = 2M(n-3) + 1: M(n) = 2²[2M(n-3) + 1] + 2 + 1 = 2³M(n-3) + 2² + 2 + 1
	- ...Continuing this pattern for _i_ substitutions: M(n) = 2ⁱM(n-i) + 2ⁱ⁻¹ + ... + 2¹ + 2⁰
	- The sum 2ⁱ⁻¹ + ... + 2¹ + 2⁰ is a geometric series equal to 2ⁱ - 1. So, M(n) = 2ⁱM(n-i) + 2ⁱ - 1.
	- We need to reach the initial condition M(1), which happens when n-i = 1, so i = n-1.
	- Substitute i = n-1: M(n) = 2ⁿ⁻¹M(n-(n-1)) + 2ⁿ⁻¹ - 1 = 2ⁿ⁻¹M(1) + 2ⁿ⁻¹ - 1.
	- Using the initial condition M(1) = 1: M(n) = 2ⁿ⁻¹(1) + 2ⁿ⁻¹ - 1 = 2ⁿ⁻¹ + 2ⁿ⁻¹ - 1 = **2ⁿ - 1**.
- Thus, the number of moves is 2ⁿ - 1, which indicates an **exponential algorithm**. This highlights that the succinctness of recursive algorithms can sometimes mask their inefficiency.

### Solve the following recurrence relations to determine their order of growth:

- a) T(n) = 2T(n/2) + n, for n > 1, T(1) = 1. (You may assume n is a power of 2). This recurrence is of the form T(n) = aT(n/b) + f(n), which can often be solved using the Master Theorem. In this case, a=2, b=2, and f(n)=n. Comparing f(n) with n^(log_b a) = n^(log_2 2) = n¹ = n. Since f(n) = n, it falls into the second case of the Master Theorem (f(n) is proportional to n^(log_b a)). The solution is T(n) ∈ Θ(n^(log_b a) * log n). Substituting the values, T(n) ∈ Θ(n¹ * log₂ n) = **Θ(n log n)**. _Note: While the sources mention the Master Theorem and solve similar recurrences, this specific application uses the standard Master Theorem form not explicitly solved step-by-step in the provided text._
	
- b) T(n) = 3T(n-1), for n > 1, T(1) = 4. We can solve this using backward substitution:
	
	- T(n) = 3T(n-1)
	- Substitute T(n-1) = 3T(n-2): T(n) = 3[3T(n-2)] = 3²T(n-2)
	- Substitute T(n-2) = 3T(n-3): T(n) = 3²[3T(n-3)] = 3³T(n-3)
	- ...Continuing this pattern for _i_ substitutions: T(n) = 3ⁱT(n-i)
	- We need to reach the initial condition T(1), which happens when n-i = 1, so i = n-1.
	- Substitute i = n-1: T(n) = 3ⁿ⁻¹T(n-(n-1)) = 3ⁿ⁻¹T(1).
	- Using the initial condition T(1) = 4: T(n) = 3ⁿ⁻¹ * 4.
	- The order of growth is determined by the exponential term. T(n) ∈ **Θ(3ⁿ)**. _Note: The sources demonstrate backward substitution for similar linear recurrences like M(n) = M(n-1) + 1 and A(n) = 2A(n-1) + 1._

### Set up and solve the recurrence relation for the time complexity of computing `n!` (factorial) using a recursive algorithm.

- The recursive algorithm for computing _n!_ is given as:
	
	```
	ALGORITHM F(n)
	//Computes n! recursively
	//Input: A nonnegative integer n
	//Output: The value of n!
	if n = 0 return 1
	else return F(n - 1) * n
	```
	
- We can take _n_ as the input size. The basic operation is multiplication. Let _M(n)_ be the number of multiplications to compute _n!_ recursively.
- To compute _F(n)_ for _n > 0_, the algorithm first computes _F(n-1)_ (which requires _M(n-1)_ multiplications) and then performs one more multiplication to get _F(n-1) * n_.
- This gives the recurrence relation: **M(n) = M(n - 1) + 1 for n > 0**.
- The base case is for _n = 0_, where the algorithm returns 1 and performs no multiplications. So, the initial condition is **M(0) = 0**.
- We can solve this recurrence using backward substitutions:
	- M(n) = M(n-1) + 1
	- Substitute M(n-1) = M(n-2) + 1: M(n) = [M(n-2) + 1] + 1 = M(n-2) + 2
	- Substitute M(n-2) = M(n-3) + 1: M(n) = [M(n-3) + 1] + 2 = M(n-3) + 3
	- ...Continuing this pattern for _i_ substitutions: M(n) = M(n-i) + i
	- We need to reach the initial condition M(0), which happens when n-i = 0, so i = n.
	- Substitute i = n: M(n) = M(n-n) + n = M(0) + n.
	- Using the initial condition M(0) = 0: M(n) = 0 + n = **n**.
- Thus, the recursive factorial algorithm performs _n_ multiplications. This makes it a **linear algorithm** as a function of _n_. However, compared to a straightforward non-recursive (iterative) calculation, the recursive version has the overhead of time and space used for maintaining the recursion's stack.

### Design and explain the Sequential Search algorithm. Analyze its time complexity for best-case, worst-case, and average-case scenarios.

- **Algorithm Description:** Sequential search is a straightforward algorithm that searches for a given value (a search key _K_) in a list of _n_ elements by checking successive elements of the list. It continues until either a match with the search key is found or the list is exhausted. Here is a pseudocode assuming the list is implemented as an array `A[0..n-1]`:
	
```
ALGORITHM SequentialSearch(A[0..n - 1], K)
//Searches for a given value in a given array by sequential search
//Input: An array A[0..n - 1] and a search key K
//Output: The index of the first element in A that matches K
// or -1 if there are no matching elements
i ← 0
while i < n and A[i] != K do
	i ← i + 1
if i < n return i
else return -1
```
	
- **Time Complexity Analysis:** The running time of sequential search can differ for inputs of the same size _n_. The basic operation is the key comparison `A[i] != K`.
	- **Worst-Case Efficiency:** The worst case occurs when there are no matching elements or the first matching element is the last one in the list. In this scenario, the algorithm makes the largest number of key comparisons, which is _n_. So, the worst-case efficiency _Cworst(n) = n_, which is in **Θ(n)**. The worst-case analysis provides an upper bound on the running time.
	- **Best-Case Efficiency:** The best case occurs when the first element in the list matches the search key. In this scenario, the algorithm makes only one key comparison. So, the best-case efficiency _Cbest(n) = 1_, which is in **Θ(1)**.
	- **Average-Case Efficiency:** To analyze the average-case efficiency, assumptions are typically made about the inputs. Common assumptions are that the probability of a successful search is _p_ (where 0 ≤ p ≤ 1) and that if the search is successful, the probability of the first match being at any position _i_ is uniform (1/n). If the search is unsuccessful (with probability 1-p), the algorithm makes _n_ comparisons. If successful at position _i_ (with probability p/n), it makes _i_ comparisons. The average number of comparisons _Cavg(n)_ is calculated as the sum of (comparisons * probability of that scenario): _Cavg(n) = ∑ (i * p/n) for i=1 to n (successful search) + (n * (1-p)) (unsuccessful search)_ _Cavg(n) = (p/n) * ∑ i (for i=1 to n) + n(1-p)_ _Cavg(n) = (p/n) * (n(n+1)/2) + n(1-p)_ _Cavg(n) = p(n+1)/2 + n(1-p)_ This can be rewritten as _pn/2 + p/2 + n - pn = n(1 - p/2) + p/2_. If p=1 (search is always successful), Cavg(n) = (n+1)/2, which is in Θ(n). If p=0 (search is always unsuccessful), Cavg(n) = n, also in Θ(n). Regardless of the probability _p_, the average-case efficiency of sequential search is in **Θ(n)**. The average-case analysis provides information about behavior on typical inputs.

### Justify the statement: “More than one algorithmic method can be used for solving the same problem.” Do this by:

- The sources explicitly state that **the same problem can often be solved by several algorithms**. These algorithms can differ in their underlying ideas, level of sophistication, and efficiency. The ubiquitousness of algorithms in daily life, not just mathematical problems, further strengthens the motivation to learn about different algorithms.
	
- **a) Describing two distinct algorithms for computing the Greatest Common Divisor (GCD):**
	
	- **Euclid's Algorithm:** This ancient algorithm computes the greatest common divisor of two nonnegative integers _m_ and _n_ (not both zero). It is based on repeatedly applying the equality gcd(_m_, _n_) = gcd(_n_, _m_ mod _n_). The steps are:
		- Step 1: If _n_ = 0, return _m_ as the answer and stop; otherwise, proceed to Step 2.
		- Step 2: Divide _m_ by _n_ and assign the remainder to _r_.
		- Step 3: Assign the value of _n_ to _m_ and the value of _r_ to _n_. Go to Step 1. This algorithm is guaranteed to stop because the second integer in the pair decreases with each iteration (since _m_ mod _n_ is always smaller than _n_) and cannot become negative, eventually reaching 0. The correctness stems from the equality gcd(_m_, _n_) = gcd(_n_, _m_ mod _n_).
	- **Consecutive Integer Checking Algorithm:** This method for computing gcd(_m_, _n_) is based on the definition of the greatest common divisor as the largest integer that divides both _m_ and _n_ evenly. Such a common divisor cannot be greater than the smaller of the two numbers, _t = min{m, n}_. The steps are:
		- Step 1: Assign the value of _min{m, n}_ to _t_.
		- Step 2: Divide _m_ by _t_. If the remainder is 0, go to Step 3; otherwise, go to Step 4.
		- Step 3: Divide _n_ by _t_. If the remainder is 0, return _t_ as the answer and stop; otherwise, proceed to Step 4.
		- Step 4: Decrease the value of _t_ by 1. Go to Step 2. This process will eventually stop because _t_ is decreased by 1 in each iteration. Since 1 divides every integer, _t_ will eventually reach a common divisor (at least 1), and the algorithm will stop. Unlike Euclid's algorithm, this version may not work correctly if one input is zero, emphasizing the importance of specifying input ranges.
- **b) Analyzing and comparing these two algorithms:**
	
	- **Ideas:** Euclid's algorithm is based on a mathematical property (the equality gcd(_m_, _n_) = gcd(_n_, _m_ mod _n_)) that reduces the problem size quickly. The consecutive integer checking algorithm is based directly on the definition of GCD and proceeds by trial and error from the largest possible candidate down.
	- **Efficiency:** The consecutive integer checking algorithm requires a division of _m_ by _t_ and a division of _n_ by _t_ for each value of _t_ from _min{m, n}_ down to gcd(_m_, _n_). In the worst case (when the GCD is small, e.g., 1), _t_ will decrease from _min{m, n}_ down to 1, requiring roughly _min{m, n}_ iterations. Euclid's algorithm reduces the size of the numbers much faster. For instance, applying Euclid's algorithm to gcd(31415, 14142) requires only 11 divisions [227a], while the consecutive integer checking algorithm would require checking values from 14142 down to 1, potentially making up to 2 * 14142 divisions (depending on how the loop is structured) [227b]. Euclid's algorithm is estimated to be between approximately 1300 and 2600 times faster for this input [227b]. Euclid's algorithm has a logarithmic time efficiency, while consecutive integer checking is linear in the value of _min{m, n}_.
	- **Simplicity:** Simplicity can be subjective. Most people might agree that Euclid's algorithm is simpler than the middle-school procedure (which involves prime factorization), but it's less clear if it's simpler than the consecutive integer checking algorithm. Simpler algorithms are generally easier to understand and program.
	- **Correctness/Robustness:** Euclid's algorithm, as presented in the sources, handles inputs where one number is zero correctly (as per the definition of GCD). The consecutive integer checking method requires careful specification of inputs to handle zeros.

### Illustrate the prime factorization method to find the GCD of two specific numbers, for example, 180 and 30.

1. Find the prime factorization of the first number, 180. 180 = 10 * 18 = (2 * 5) * (2 * 9) = 2 * 5 * 2 * 3 * 3 = 2² * 3² * 5¹
2. Find the prime factorization of the second number, 30. 30 = 3 * 10 = 3 * (2 * 5) = 2¹ * 3¹ * 5¹
3. Identify the common prime factors and their lowest powers present in both factorizations. Common factors are 2, 3, and 5. Lowest power of 2 is 2¹ (from 30). Lowest power of 3 is 3¹ (from 30). Lowest power of 5 is 5¹ (from both).
4. Multiply these common prime factors raised to their lowest powers to find the GCD. GCD(180, 30) = 2¹ * 3¹ * 5¹ = 2 * 3 * 5 = 30.