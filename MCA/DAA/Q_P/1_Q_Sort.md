

**I. Notion of Algorithm**

1.  Define an algorithm and explain its fundamental characteristics (e.g., finiteness, definiteness, input, output, effectiveness).
2.  What are the properties or characteristics of a "good" algorithm?
3.  Discuss why the study of algorithms is important in computer science.
4.  Justify the statement: "An algorithm is a notion."
5.  Provide an example of a simple real-world process that can be described as an algorithm.
6.  Differentiate between an algorithm and a program.

---

**II. Fundamentals of Algorithmic Problem Solving**

1.  Outline and explain the general steps involved in the algorithm design and analysis process. You may use a flowchart to illustrate this.
2.  Describe the typical sequence of steps undertaken for algorithmic problem-solving, from understanding the problem to implementing and testing the solution.
3.  What does it mean to prove the correctness of an algorithm? Why is it important?

---

**III. Important Problem Types**

1.  List and briefly explain common categories of algorithmic problems (e.g., sorting, searching, string processing, graph problems, combinatorial problems, geometric problems, numerical problems).
2.  Describe the two primary methods for representing graphs in computer memory (e.g., adjacency matrix, adjacency lists). Provide an example for each method.
3.  Explain the concepts of a graph and a weighted graph, using examples.

---

**IV. Fundamentals of the Analysis of Algorithm Efficiency**

**A. Analysis Framework**
1.  Define what is meant by the time complexity and space complexity of an algorithm.
2.  Explain the concepts of worst-case, best-case, and average-case efficiency analysis for algorithms.
3.  Provide an example of an algorithm and discuss its best-case, worst-case, and average-case scenarios.
4.  Justify why worst-case analysis is often considered more important than average-case analysis in the study of algorithms.


5.  What is meant by the "input size" of an algorithm? How is it typically measured for problems like sorting, matrix multiplication, or graph traversal?
6.  Define the "running time" of an algorithm. What factors can influence it?
7.  What is the "order of growth" of an algorithm's running time? Why is it a crucial concept for comparing algorithms?
8.  What are the basic operations considered when analyzing the efficiency of an algorithm?

**B. Asymptotic Notations and Basic Efficiency Classes**
1.  Define Big O (O), Big Omega (Ω), and Big Theta (Θ) notations. Explain the significance of each in analyzing algorithm efficiency.
2.  Provide examples for each asymptotic notation (O, Ω, Θ).
3.  Explain why asymptotic notations are necessary or beneficial in algorithm analysis.
4.  Discuss the formal definitions of O, Ω, and Θ notations.

5.  Explain the practical significance of using asymptotic notations in algorithm analysis.
6.  List and describe the basic asymptotic efficiency classes (e.g., constant, logarithmic, linear, n log n, quadratic, cubic, exponential). Provide an example algorithm for each if possible.
7.  Compare and contrast O, Ω, and Θ notations.
8.  If an algorithm has a time complexity of O(n^2), can we also say it is O(n^3)? Explain.
9.  If an algorithm has a time complexity of Θ(n), can we also say it is O(n^2)? Explain.


10.  Prove the property: If t₁(n) ∈ O(g₁(n)) and t₂(n) ∈ O(g₂(n)), then t₁(n) + t₂(n) ∈ O(max{g₁(n), g₂(n)}).
11.  For each of the following functions, indicate how its value changes if its input `n` is increased eightfold:
    a) log₂n
    b) n
    c) n²
    d) n³
    e) 2ⁿ
12.  Compare the order of growth for the following pairs of functions. State whether the first function has a smaller, larger, or the same order of growth as the second:
    a) n(n+1) and 200n⁴
    b) 2^(n-1) and 2ⁿ
13.  For the following functions, express their complexity using Big O, Big Omega, and Big Theta notation:
    a) f(n) = 10n³ + 8
    b) g(n) = 100n + 5
14.  Arrange the following functions in ascending order of their growth rates:
    (n-2)!, 5lg(n+100)¹⁰, 2²ⁿ, 0.001n⁴+3n³+1, ln²n, ³√n, 3ⁿ.
15. Using the definitions of O, Θ, and Ω, determine whether the following assertions are true or false. Justify your answers.
    a) n(n+1)/2 ∈ O(n³)
    b) n(n+1)/2 ∈ Θ(n³)
    c) n(n+1)/2 ∈ Ω(n)
16. List and explain the basic asymptotic efficiency classes (e.g., constant, logarithmic, linear, n log n, quadratic, cubic, exponential). Provide an example algorithm or function for each class and list them in ascending order of growth.

**C. Mathematical Analysis of Non-Recursive Algorithms**
1.  Outline the general plan or steps for analyzing the time efficiency of non-recursive algorithms.
2.  Develop an algorithm for the "element uniqueness problem" (checking if all elements in a given array are distinct) and derive its time complexity.
3.  Consider the following algorithm:
    ```
    ALGORITHM Sum(n)
    // Input: A non-negative integer n
    Sum ← 0
    For i ← 1 to n do
        Sum ← Sum + i
    Return Sum
    ```
    a) What task does this algorithm perform?
    b) Identify the basic operation.
    c) Determine how many times the basic operation is executed as a function of `n`.
4.  Develop an algorithm for multiplying two `n x n` matrices and analyze its time complexity.
5.  Write a non-recursive algorithm to compute the factorial of a given non-negative integer `n` and analyze its time efficiency.
6.  Design a non-recursive algorithm to compute the sum of the squares of the first ‘n’ natural numbers (i.e., 1² + 2² + ... + n²). Analyze its time complexity.
7.  Analyze the time complexity of an algorithm that finds the maximum element in an array of `n` numbers.
8.  How do you analyze algorithms with nested loops? Provide an example.


**D. Mathematical Analysis of Recursive Algorithms**
1.  What is a recurrence relation? How is it used to describe the efficiency of recursive algorithms?
2.  Describe the general plan or steps for analyzing the time efficiency of recursive algorithms.
3.  Explain the recursive algorithm for the Towers of Hanoi problem.
4.  Set up the recurrence relation for the number of moves in the Towers of Hanoi problem and solve it to determine the algorithm's time efficiency.
5.  Solve the following recurrence relations to determine their order of growth:
    a) T(n) = 2T(n/2) + n, for n > 1, T(1) = 1. (You may assume n is a power of 2).
    b) T(n) = 3T(n-1), for n > 1, T(1) = 4.

6.  Set up and solve the recurrence relation for the time complexity of computing `n!` (factorial) using a recursive algorithm.
7.  State the Master Theorem. Explain its components and when it can be applied to solve recurrence relations.
8.  Use the Master Theorem (if applicable) to find the time complexity for T(n) = 2T(n/2) + n.
9.  Use the Master Theorem (if applicable) to find the time complexity for T(n) = T(n/2) + 1.

**E. Examples**
1.  Design and explain the Sequential Search algorithm. Analyze its time complexity for best-case, worst-case, and average-case scenarios.
2.  Justify the statement: “More than one algorithmic method can be used for solving the same problem.” Do this by:
    a) Describing two distinct algorithms for computing the Greatest Common Divisor (GCD) of two integers (e.g., Euclid's algorithm, prime factorization, or consecutive integer checking).
    b) Analyzing and comparing these two algorithms, discussing their pros, cons, or relative efficiencies.
3.  Illustrate the prime factorization method to find the GCD of two specific numbers, for example, 180 and 30.

---



