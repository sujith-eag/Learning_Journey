
## Analysis Framework

### Define what is meant by the time complexity and space complexity of an algorithm.

The efficiency of an algorithm can be measured in two principal ways: time efficiency and space efficiency.

- **Time complexity**, also referred to as **time efficiency**, indicates how fast an algorithm runs. It is typically measured as a function of the algorithm's input size by counting the number of times its **basic operation** is executed. 

- The basic operation is usually the most time-consuming operation in the algorithm's innermost loop and contributes the most to the total running time. This measure is preferred over using standard time units (like seconds) because it is independent of the speed of a particular computer, the quality of the implementation, and the compiler used.

- **Space complexity**, or **space efficiency**, refers to the amount of memory units required by the algorithm. This includes the extra memory used by the algorithm in addition to the space needed for its input and output. 

- While in the early days of computing both time and space were at a premium, advancements have made space less of a concern in many modern applications, though it still matters due to different memory tiers (main, secondary, cache).

The analysis framework often focuses primarily on time efficiency. Both time and space efficiencies are measured as functions of the algorithm's input size.

### Explain the concepts of worst-case, best-case, and average-case efficiency analysis for algorithms.

For many algorithms, the running time is not solely dependent on the input size but also on the specific characteristics of the input. To address this, efficiency analysis distinguishes between different scenarios:

- **Worst-case efficiency** refers to the algorithm's efficiency for the worst-case input of a specific size _n_. This is the input (or inputs) of size _n_ for which the algorithm runs the **longest** among all possible inputs of that size. 
- Determining this involves analyzing the algorithm to find the input that maximizes the basic operation's count, C(n). 
- The worst-case analysis is crucial as it provides an upper bound on the running time, guaranteeing that for any instance of size _n_, the running time will not exceed this value.

- **Best-case efficiency** is the algorithm's efficiency for the best-case input of size _n_. This is the input (or inputs) of size _n_ for which the algorithm runs the **fastest** among all possible inputs of that size. 
- Analyzing this involves identifying the input for which the basic operation count C(n) is smallest. 
- While less critical than worst-case, it's not entirely useless; for some algorithms, a good best-case performance extends to inputs that are "almost" best-case, making them suitable for specific applications (like insertion sort for almost-sorted arrays). If the best-case is poor, the algorithm can be discarded.

- **Average-case efficiency** seeks to provide information about the algorithm's behavior on a "typical" or "random" input. 
- Analyzing this is generally more difficult than worst-case or best-case analysis. It requires making assumptions about the probability distribution of inputs of size _n_ and then calculating the expected value of the basic operation count. 
- This analysis is essential because for many important algorithms, the average-case efficiency is significantly better than the pessimistic worst-case suggests.


### Provide an example of an algorithm and discuss its best-case, worst-case, and average-case scenarios.
    
**Sequential Search** algorithm searches for a given value (a search key _K_) in a list (or array) of _n_ elements by checking the elements one after another until either the key is found or the list is exhausted. The basic operation is the **key comparison** (e.g., comparing `A[i]` with `K`).

```
ALGORITHM  SequentialSearch(A[0..n − 1], K)
//Searches for a given value in a given array by sequential search

//Input: An array A[0..n − 1] and a search key K
//Output: The index of the first element in A that matches K
// or −1 if there are no matching elements

i←0
while i < n and A[i] /= K do
	i ← i+1
if i < n return i
else return -1
```

Let's consider the algorithm `SequentialSearch(A[0..n-1], K)`:

- **Worst-case scenario:** The algorithm makes the largest number of key comparisons when the search key _K_ is **not present** in the list or when it is the **very last element** (`A[n-1]`). In either case, the algorithm has to compare the key with every element in the list. The number of comparisons is `Cworst(n) = n`.

- **Best-case scenario:** The algorithm runs fastest when the search key _K_ is found at the **very first position** of the list (`A`). Only one comparison is needed to find the key. The number of comparisons is `Cbest(n) = 1`.

- **Average-case scenario:** Analyzing the average case requires assumptions about the inputs. A standard assumption is that there's a probability _p_ (0 ≤ _p_ ≤ 1) of a successful search, and if successful, the key is equally likely to be in any position _i_ (0 to _n_-1). The number of comparisons in a successful search at position _i_ is _i_+1. The probability of this is _p/n_. In an unsuccessful search (probability 1-_p_), the algorithm makes _n_ comparisons. The average number of comparisons `Cavg(n)` is calculated as the sum of (comparisons * probability) over all possibilities: `Cavg(n) = [∑(i+1) * (p/n) for i from 0 to n-1] + [n * (1-p)]`. This simplifies to `Cavg(n) = p*(n+1)/2 + n*(1-p)`. As you can see, the average case analysis is more complex and depends on the assumed probability _p_.

### Justify why worst-case analysis is often considered more important than average-case analysis in the study of algorithms.
    
While average-case analysis can provide valuable insight into an algorithm's performance on typical inputs and may reveal that it is much better than the worst-case suggests for some algorithms, **worst-case analysis is often considered more important due to the strong guarantees it provides**.

- **Guaranteed Upper Bound:** The primary reason is that the worst-case analysis establishes a guaranteed upper bound on the algorithm's running time for any valid input of a given size. This is critical in many applications where the algorithm's performance cannot afford to degrade significantly, such as real-time systems, safety-critical software, or competitive programming where exceeding time limits means failure. Knowing the maximum possible time ensures that the algorithm will meet performance requirements regardless of the specific input.

- **Limitations of Other Cases:**
	- The best-case efficiency is usually not representative of typical performance, as it often occurs for specific, sometimes trivial, inputs that are unlikely to be encountered frequently in practice.
	- Average-case analysis, while informative, often relies on making assumptions about the distribution of inputs. These assumptions can be difficult to validate in real-world scenarios, and if the actual input distribution differs from the assumption, the average-case prediction may be inaccurate. Furthermore, performing average-case analysis is technically more challenging.

In summary, the **guarantee of performance** provided by the worst-case analysis is often paramount, ensuring that the algorithm will never perform worse than a certain threshold, making it a more reliable metric for evaluating algorithmic performance in many practical and theoretical contexts compared to the best-case or potentially less certain average-case analyses.


## B. Asymptotic Notations and Basic Efficiency Classes


### Define Big O (O), Big Omega (Ω), and Big Theta (Θ) notations. Explain the significance of each in analyzing algorithm efficiency.
    
Asymptotic notations are the language used by computer scientists to **compare and rank the orders of growth of functions expressing algorithm efficiencies**. They focus on how an algorithm's performance (time or space) scales as the input size _n_ goes to infinity.

- **Big O (O) Notation (Upper Bound):**: Informally, O(g(n)) represents the set of all functions with a **lower or the same order of growth as g(n)** (to within a constant multiple). 

* `f(n) = O(g(n))` means that `f(n)` grows **no faster than** `g(n)` (up to a constant factor) for sufficiently large `n`. Its significance is that it provides an **upper bound** on the algorithm's efficiency.

* Big O notation is most commonly used to describe the **worst-case time complexity** of an algorithm. It tells us the maximum amount of time an algorithm might take for a given input size, providing a guarantee that the algorithm will not perform worse than this bound. This is crucial for understanding performance limits and making choices between algorithms, especially for applications where worst-case performance is critical.

- **Big Omega (Ω) Notation (Lower Bound):**: Informally, Ω(g(n)) represents the set of all functions with a **higher or the same order of growth as g(n)** (to within a constant multiple). Its significance is that it provides a **lower bound** on the algorithm's efficiency. 

* `f(n) = Ω(g(n))` means that `f(n)` grows **at least as fast as** `g(n)` (up to a constant factor) for sufficiently large `n`. `g(n)` provides an **asymptotic lower bound** for `f(n)`.

* Big Omega notation is often used to describe the **best-case time complexity** of an algorithm. It tells us the minimum amount of time an algorithm will take for a given input size.

- **Big Theta (Θ) Notation (Tight Bound):**: Informally, Θ(g(n)) represents the set of all functions that have the **same order of growth as g(n)** (to within a constant multiple). Its significance is that it characterizes the **exact order of growth** of the algorithm's efficiency. 

* `f(n) = Θ(g(n))` means that `f(n)` grows **at the same rate as** `g(n)` (up to constant factors) for sufficiently large `n`. `g(n)` provides both an **asymptotic upper bound and an asymptotic lower bound** for `f(n)`.

* Big Theta notation provides the most precise description of an algorithm's growth rate. It indicates that the algorithm's running time is tightly bound by `g(n)`. This is often used to describe the **average-case complexity** or when the best-case and worst-case complexities are the same. When we say an algorithm is "Θ(n²)", it means its performance is quadratic, not better and not worse in terms of growth rate.


### Provide examples for each asymptotic notation (O, Ω, Θ).

**Big O (O)**:
- `n ∈ O(n²)` (linear function has lower order of growth than quadratic)
- `100n + 5 ∈ O(n²)` (linear function has lower order of growth than quadratic)
- `½n(n − 1) ∈ O(n²)` (quadratic function has the same order of growth as quadratic)
- `n³ ∈ O(n²)` (cubic function does _not_ have lower or the same order of growth as quadratic)
- `log₂ n ∈ O(√n)` (logarithmic function has a smaller order of growth than square root)

*   If `f(n) = 3n + 5`, then `f(n) = O(n)`.
	*   *Explanation:* For large `n`, `3n + 5` is bounded above by `c*n` (e.g., `4n`).
*   If `f(n) = 2n² + 10n + 3`, then `f(n) = O(n²)`.
	*   *Explanation:* The `n²` term dominates for large `n`. We can find a constant `c` such that `2n² + 10n + 3 ≤ c*n²`.
*   If `f(n) = 5`, then `f(n) = O(1)` (constant time).
*   `n = O(n²)`, because `n` grows slower than `n²`.
*   `n log n = O(n²)`, because `n log n` grows slower than `n²`.

**Big Omega (Ω)**:
- `n³ ∈ (n²)` (cubic function has a higher order of growth than quadratic)
- `½n(n − 1) ∈ (n²)` (quadratic function has the same order of growth as quadratic)
- `100n + 5 ∈ (n²)` (linear function does _not_ have higher or the same order of growth as quadratic)
- `n! ∈ (2ⁿ)` (factorial function has a larger order of growth than exponential)

*   If `f(n) = 3n + 5`, then `f(n) = Ω(n)`.
	*   *Explanation:* For large `n`, `3n + 5` is bounded below by `c*n` (e.g., `1n`).
*   If `f(n) = 2n² + 10n + 3`, then `f(n) = Ω(n²)`.
	*   *Explanation:* The `n²` term dominates, and `2n² + 10n + 3 ≥ c*n²` for some constant `c > 0`.
*   If `f(n) = 100n`, then `f(n) = Ω(n)`.
*   `n² = Ω(n)`, because `n²` grows faster than `n`.
*   `2ⁿ = Ω(n²)`, because `2ⁿ` (exponential) grows much faster than `n²` (polynomial).


**Big Theta (Θ)**:
- Any quadratic function `an² + bn + c` with `a > 0` is in (n²).
- `½n(n − 1) ∈ (n²)`.
- `log₂ n ∈ (log n)` (logarithms with different bases have the same order of growth, just differ by a constant multiplicative factor).

*   If `f(n) = 3n + 5`, then `f(n) = Θ(n)`.
	*   *Explanation:* `3n + 5` is bounded both above and below by constant multiples of `n` for large `n`.
*   If `f(n) = 2n² + 10n + 3`, then `f(n) = Θ(n²)`.
	*   *Explanation:* It's both `O(n²)` and `Ω(n²)`.
*   If `f(n) = (1/2)n log n + 7n - 100`, then `f(n) = Θ(n log n)`.
*   `n` is **not** `Θ(n²)`, because while `n = O(n²)`, `n` is not `Ω(n²)`.
*   `5n³ + 2n² - n + 1000 = Θ(n³)`.

### Explain why asymptotic notations are necessary or beneficial in algorithm analysis.
    
Asymptotic notations are essential because they allow us to analyze algorithm efficiency in a way that is **independent of specific computer hardware, software implementations, or compilers**. Instead of measuring time in seconds (which varies greatly), we count the number of times a **basic operation** is executed as a function of input size _n_.

- The running time (or space) function of an algorithm can be complex, often involving lower-order terms and multiplicative constants. Asymptotic notations allow us to **ignore these less significant factors** for large inputs and focus on the **dominant term**. For instance, an algorithm with time complexity `½n² - ½n` is considered (n²) because for large _n_, the `½n²` term dominates.
- This emphasis on the order of growth for large inputs is crucial because the performance difference between algorithms with different orders of growth becomes **clear and important only when dealing with large problem sizes**. A difference in running times on small inputs is not what truly distinguishes efficient algorithms from inefficient ones.
- By using asymptotic notations, we can **classify algorithms into basic efficiency classes** (like linear, quadratic, logarithmic, exponential). This classification provides a powerful way to **compare algorithms** for the same problem. Generally, an algorithm belonging to a better asymptotic efficiency class (e.g., linear vs. quadratic) will outperform one from a worse class for moderately sized inputs, even if the constant factors differ.

In essence, asymptotic notations provide a **standard, robust, and high-level way to describe and compare the efficiency of algorithms**, focusing on how their resource requirements scale with increasing input size, which is the most important factor for large problems.




### For each of the following functions, indicate how its value changes if its input `n` is increased eightfold:

This question relates to how functions scale with input size. 

- a) **log₂n**: If `n` is increased eightfold to `8n`, the new value is `log₂(8n)`. Using logarithm properties, `log₂(8n) = log₂8 + log₂n = 3 + log₂n`. So, the value **increases by 3**.  `log₂ n` increases by just 1 with a twofold increase in `n`.

- b) **n**: If `n` is increased eightfold to `8n`, the new value is `8n`. The value **increases eightfold**.

- c) **n²**: If `n` is increased eightfold to `8n`, the new value is `(8n)² = 64n²`. The value **increases 64-fold**. Quadratic function `n²` increases fourfold with a twofold increase in `n`.
- d) **n³**: If `n` is increased eightfold to `8n`, the new value is `(8n)³ = 512n³`. The value **increases 512-fold**. Cubic function `n³` increases eightfold with a twofold increase in `n`.

- e) **2ⁿ**: If `n` is increased eightfold to `8n`, the new value is `2⁸ⁿ = (2ⁿ)⁸`. The value **is raised to the power of 8**. Value of `2ⁿ` gets squared (`(2ⁿ)²`) with a twofold increase in `n`.

### Compare the order of growth for the following pairs of functions. State whether the first function has a smaller, larger, or the same order of growth as the second:

The order of growth refers to how the function scales as the input size `n` goes to infinity, ignoring constant multiples and lower-order terms. We can use informal comparison or limits.

a) **n(n+1) and 200n⁴**:
- `n(n+1) = n² + n`. As `n` approaches infinity, the dominant term is `n²`. This function is in Θ(n²).
- `200n⁴`. As `n` approaches infinity, the dominant term is `200n⁴`. This function is in Θ(n⁴).
- Comparing `n²` and `n⁴`, the function `n⁴` grows faster than `n²`. `100n²` (quadratic) has a lower order of growth than `0.01n³` (cubic). Similarly, quadratic grows slower than quartic.
- Therefore, the first function `n(n+1)` has a **smaller** order of growth than the second function `200n⁴`.

b) **2ⁿ⁻¹ and 2ⁿ**:
- `2ⁿ⁻¹ = 2ⁿ * 2⁻¹ = ½ * 2ⁿ`.
- The two functions differ only by a constant multiplicative factor (½).
- Therefore, the first function `2ⁿ⁻¹` has the **same** order of growth as the second function `2ⁿ`.


### For the following functions, express their complexity using Big O, Big Omega, and Big Theta notation:

For a function t(n), O(g(n)) provides an upper bound, Ω(g(n)) provides a lower bound, and Θ(g(n)) provides a tight bound (same order of growth),. For polynomials with a positive leading coefficient, the order of growth is determined by the highest degree term. The simplest function g(n) is typically used in these notations.

- a) **f(n) = 10n³ + 8**:
    
    - This is a polynomial of degree 3. The highest degree term is `10n³`.
    - The function's order of growth is the same as `n³`.
    - Using Big Theta: `f(n) ∈ Θ(n³)` . This means it's bounded above and below by constant multiples of `n³` for large `n`.
    - Using Big O: Since `f(n)` is in `Θ(n³)`, it is also in `O(n³)`. It is bounded above by a constant multiple of `n³` for large `n`.
    - Using Big Omega: Since `f(n)` is in `Θ(n³)`, it is also in `Ω(n³)`. It is bounded below by a positive constant multiple of `n³` for large `n`.

- b) **g(n) = 100n + 5**:
    
    - This is a polynomial of degree 1. The highest degree term is `100n`.
    - The function's order of growth is the same as `n`.
    - Using Big Theta: `g(n) ∈ Θ(n)`. It's bounded above and below by constant multiples of `n` for large `n`.
    - Using Big O: Since `g(n)` is in `Θ(n)`, it is also in `O(n)`. It is bounded above by a constant multiple of `n` for large `n`.
    - Using Big Omega: Since `g(n)` is in `Θ(n)`, it is also in `Ω(n)`. It is bounded below by a positive constant multiple of `n` for large `n`.

### Arrange the following functions in ascending order of their growth rates: 
`(n-2)!, 5lg(n+100)¹⁰, 2²ⁿ, 0.001n⁴+3n³+1, ln²n, ³√n, 3ⁿ.`

We need to determine the dominant term or recognized growth class for each function and then order them,,.

- `5lg(n+100)¹⁰ = 50 lg(n+100)`: This is logarithmic. Logarithms with different bases belong to the same efficiency class (Θ(log n)) .
- `ln²n = (ln n)²`: This is a squared logarithmic function. Θ(log² n). As `n` grows, log²n grows faster than log n .
- `³√n = n^(1/3)`: This is a polynomial with a fractional exponent. Θ(n^(1/3)). Polynomials grow faster than logarithms .
- `0.001n⁴+3n³+1`: This is a polynomial of degree 4. The highest degree term dominates for large `n`. Θ(n⁴) . Polynomials grow faster than `n^(1/3)`.
- `3ⁿ`: This is an exponential function with base 3. Θ(3ⁿ). Exponential functions grow faster than any polynomial.
- `2²ⁿ = (2²)ⁿ = 4ⁿ`: This is an exponential function with base 4. Θ(4ⁿ). Comparing exponential functions `aⁿ` and `bⁿ` where `a < b`, `bⁿ` grows faster than `aⁿ`. So `4ⁿ` grows faster than `3ⁿ`.
- `(n-2)!`: This is a factorial function. Θ((n-2)!). Factorial functions grow much faster than exponential functions,,.

Arranging them in ascending order of growth rates:

1. `5lg(n+100)¹⁰` (Θ(log n))
2. `ln²n` (Θ(log² n))
3. `³√n` (Θ(n^(1/3)))
4. `0.001n⁴+3n³+1` (Θ(n⁴))
5. `3ⁿ` (Θ(3ⁿ))
6. `2²ⁿ` (Θ(4ⁿ))
7. `(n-2)!` (Θ((n-2)!))

This matches the ordering given in the source.

**15. Using the definitions of O, Θ, and Ω, determine whether the following assertions are true or false. Justify your answers.**

Recall the formal definitions:

- t(n) ∈ O(g(n)) if t(n) ≤ c * g(n) for n ≥ n₀ for some positive constant c and nonnegative n₀.
- t(n) ∈ Ω(g(n)) if t(n) ≥ c * g(n) for n ≥ n₀ for some positive constant c and nonnegative n₀.
- t(n) ∈ Θ(g(n)) if c₂ * g(n) ≤ t(n) ≤ c₁ * g(n) for n ≥ n₀ for some positive constants c₁, c₂ and nonnegative n₀.

The function in question is `t(n) = n(n+1)/2 = ½n² + ½n`. This function has an order of growth of n²,. Thus, t(n) ∈ Θ(n²).

- a) **n(n+1)/2 ∈ O(n³)**:
    
    - **True**. `O(n³)` is an upper bound. Since `½n² + ½n` grows slower than `n³`, it is bounded above by a constant multiple of `n³` for large `n`,.
    - Justification using definition: We need to find `c > 0` and `n₀ ≥ 0` such that `½n² + ½n ≤ c * n³` for all `n ≥ n₀`. For `n ≥ 1`, `½n² + ½n ≤ ½n³ + ½n³ = n³`. We can choose `c=1` and `n₀=1`.

- b) **n(n+1)/2 ∈ Θ(n³)**:    
    - **False**. `Θ(n³)` implies the same order of growth as `n³`. `½n² + ½n` has a lower order of growth than `n³`.
    - Justification using definition: We need to show that there do _not_ exist positive constants `c₁`, `c₂` and nonnegative `n₀` such that `c₂ * n³ ≤ ½n² + ½n ≤ c₁ * n³` for all `n ≥ n₀`. Specifically, the lower bound `c₂ * n³ ≤ ½n² + ½n` cannot hold for any positive `c₂` for sufficiently large `n`, because `n³` grows faster than `n²`.
	
- c) **n(n+1)/2 ∈ Ω(n)**:
    
    - **True**. `Ω(n)` is a lower bound. Since `½n² + ½n` grows faster than `n` (for large n), it is bounded below by a positive constant multiple of `n` for large `n`,.
    - Justification using definition: We need to find `c > 0` and `n₀ ≥ 0` such that `½n² + ½n ≥ c * n` for all `n ≥ n₀`. For `n ≥ 0`, `½n² + ½n ≥ ½n`. We can choose `c=½` and `n₀=0`. 

### List and explain the basic asymptotic efficiency classes (e.g., constant, logarithmic, linear, n log n, quadratic, cubic, exponential). Provide an example algorithm or function for each class and list them in ascending order of growth.

Asymptotic efficiency classes classify algorithms based on how their running time (or space) grows as the input size increases without bound,. The primary interest is in the order of growth for large input sizes. These classes ignore constant factors and lower-order terms.

Here are the basic classes in ascending order of growth,-,:

- **Constant (Θ(1))**: The running time is constant, independent of the input size `n`, for sufficiently large `n`.
    - _Explanation:_ The number of basic operations is bounded by a constant.
    - _Example Algorithm/Function:_ Accessing an element in an array by its index [36a]. Finding the minimum or maximum element in a _sorted_ array [253b]. Best-case efficiency of sequential search (when the element is found first), [243b]. Deleting the i-th element from an unsorted array if allowed to replace it with the last element [36a].
- **Logarithmic (Θ(log n))**: The running time grows as the logarithm of the input size. This is typically seen in algorithms that repeatedly halve the problem size. The base of the logarithm does not affect the efficiency class, [69c].
    - _Explanation:_ For an input size `n`, the algorithm performs roughly `log n` basic operations.
    - _Example Algorithm/Function:_ Binary search in a sorted array, [371c]. Euclid's algorithm for finding the greatest common divisor, [199a]. Finding the number of bits in the binary representation of an integer `n`,, [231b].
- **Linear (Θ(n))**: The running time grows linearly with the input size.
    - _Explanation:_ The algorithm performs a number of basic operations proportional to `n`.
    - _Example Algorithm/Function:_ Sequential search in an unsorted list,, [243a]. Finding the minimum or maximum element in an unsorted array, [253a]. Computing the sum of `n` numbers [64a], [228a]. Converting a binary number to a decimal number.
- **Linearithmic (Θ(n log n))**: The running time grows as `n` times the logarithm of `n`. Often occurs in divide-and-conquer sorting algorithms.
    - _Explanation:_ The algorithm might involve iterating `n` times, with each iteration involving a logarithmic operation (or vice versa).
    - _Example Algorithm/Function:_ Mergesort (worst and average cases). Quicksort (average case). Finding the two closest numbers among `n` real numbers using presorting [445a],.
- **Quadratic (Θ(n²))**: The running time grows as the square of the input size. Typically seen in algorithms with nested loops where each loop iterates up to `n` times.
    - _Explanation:_ For an input size `n`, the algorithm performs roughly `n²` basic operations.
    - _Example Algorithm/Function:_ Selection sort,. Bubble sort,. Brute-force algorithm for the closest-pair problem. Checking if all elements in an array are unique by comparing all pairs. Definition-based matrix addition [220a].
- **Cubic (Θ(n³))**: The running time grows as the cube of the input size. Often results from algorithms with three nested loops.
    - _Explanation:_ For an input size `n`, the algorithm performs roughly `n³` basic operations.
    - _Example Algorithm/Function:_ Definition-based matrix multiplication, [221b]. Gaussian elimination, [223a].
- **Exponential (Θ(aⁿ), where a > 1)**: The running time grows as an exponential function of the input size. These algorithms quickly become impractical for even moderately sized inputs,.
    - _Explanation:_ For an input size `n`, the algorithm performs roughly `aⁿ` basic operations for some constant `a > 1`.
    - _Example Algorithm/Function:_ The recursive algorithm for computing the `n`th Fibonacci number using the definition,. The Tower of Hanoi puzzle,. Algorithms that generate all subsets of an `n`-element set.
- **Factorial (Θ(n!))**: The running time grows as the factorial of the input size. These algorithms are only practical for very small inputs,,.
    - _Explanation:_ For an input size `n`, the algorithm performs roughly `n!` basic operations.
    - _Example Algorithm/Function:_ Exhaustive search for the Traveling Salesman Problem (checking all permutations of cities). Algorithms that generate all permutations of an `n`-element set.