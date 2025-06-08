
**Brute Force:**
*   Selection Sort
*   Sequential Search (focusing on brute-force aspects if different from previous)
*   Brute-Force String Matching
*   Exhaustive Search (e.g., TSP, Knapsack as brute-force)
**Divide-and-Conquer:**
*   Merge Sort
*   Quick Sort
*   Binary Search (focusing on divide-and-conquer aspects)
**Principles of Parallel Algorithm Design:**
*   Preliminaries-Decomposition
*   Tasks and Dependency Graphs
*   Granularity
*   Concurrency and Task-Interaction
*   Decomposition Techniques

___

**V. Brute Force**

**A. General Concepts of Brute Force**
1.  Define the "Brute Force" approach to problem-solving.
2.  What are the general advantages and limitations of the Brute Force method in algorithm design?
3.  Write two key differences between the Brute Force and Divide-and-Conquer techniques of algorithm design.
4. When might a Brute Force approach be considered a practical or reasonable choice for solving a problem?


**B. Selection Sort**
1.  Describe the Selection Sort algorithm.
2.  Write a clear algorithm or pseudocode for Selection Sort.
3.  Analyze the time complexity of the Selection Sort algorithm.
4.  Trace the execution of the Selection Sort algorithm on the following lists of numbers/characters:
    *   `[81, 43, 66, 87, 21, 34, 15]`
    *   `[89, 45, 68, 90, 29, 34, 17]`
    *   `[234, 155, 409, 119, 789, 721, 345, 678]`
    *   `[S, E, Q, U, E, N, T, I, A, L]` (in alphabetical order)
    *   `[C, O, M, P, U, T, E, R]` (in alphabetical order)
    *   `[45, 90, 20, 100, 75, 30]`
    *   `[S, E, L, E, C, T, I, O, N, S, O, R, T]` (in alphabetical order)
5.  Is Selection Sort a stable sorting algorithm? Explain your answer.

**C. Brute-Force String Matching**
6.  Explain the Brute-Force String Matching algorithm.
7.  Write an algorithm or pseudocode for the Brute-Force String Matching technique.
8.  Analyze the time complexity of the Brute-Force String Matching algorithm.
9.  Trace the Brute-Force String Matching algorithm for the following scenarios:
    *   Pattern: `"COMPUTER"`, Text: `"MASTER OF COMPUTER APPLICATIONS"`
    *   Pattern: `"EE"`, Text: `"ENGINEERING COLLEGE"` (also write the steps)
    *   Pattern: `"NOT"`, Text: `"NOBODY_NOTICED_HIM"` (also determine the number of character comparisons)
    *  Pattern `P`. (e.g., T = `ABABDABACDABABCABAB`, P = `ABABCABAB`)

**D. Exhaustive Search**
1.  Define "Exhaustive Search" as an approach to problem-solving. (How does it relate to Brute force strategy)
2.  Demonstrate the use of Exhaustive Search for the Traveling Salesperson Problem (TSP) with a suitable example.
3.  Solve the following 0/1 Knapsack problem using Exhaustive Search, given a capacity W=10:

| Item | Weight | Value |
|------|--------|-------|
| 1    | 7      | $42   |
| 2    | 3      | $12   |
| 3    | 4      | $40   |
| 4    | 5      | $25   |

4.  Discuss the primary limitations of using Exhaustive Search for solving complex combinatorial problems.

---

**VI. Divide-and-Conquer**

**A. General Concepts of Divide-and-Conquer**
1.  Explain the "Divide-and-Conquer" paradigm in algorithm design. (What are the three fundamental steps involved in this strategy?)
2.  Briefly explain the method for multiplying two large integers based on the Divide-and-Conquer strategy. Analyze its time efficiency using backward substitution (or recurrence relation).
3. What characteristics make a problem well-suited for a Divide-and-Conquer approach?
4. Write down the general form of a recurrence relation that typically describes the time complexity of a Divide-and-Conquer algorithm. How is the Master Theorem often applied in this context?

**B. Merge Sort**
1.  Describe the Merge Sort algorithm, clearly explaining its divide, conquer, and combine steps.
2.  Write an algorithm or pseudocode for Merge Sort.
3.  Analyze the time complexity of Merge Sort.
4.  Is Merge Sort an in-place sorting algorithm? Is it a stable sorting algorithm? Explain.
5.  Trace the Merge Sort algorithm on the following lists of numbers:
    *   `[8, 3, 2, 9, 7, 1, 5, 4]`
    *   `[67, 23, 45, 89, 59, 34, 70, 55]`
    *   `[10, 40, 60, 90, 20, 45]` (show steps in detail and evaluate using a recursive tree)

**C. Quick Sort**
1.  Describe the Quick Sort algorithm, paying special attention to the partitioning step.
2.  Write an algorithm or pseudocode for Quick Sort.
3.  Analyze the time complexity of Quick Sort for its best-case, worst-case, and average-case scenarios (especially when the input is a set of random numbers for the average case).
4.  Trace the Quick Sort algorithm on the following lists of numbers/characters:
    *   `[5, 3, 1, 9, 8, 2, 4, 7]`
    *   `{Q, U, I, C, K, S, O, R, T}`
    *   `[55, 26, 93, 17, 77, 31, 44, 55, 20]`

5.  Explain what conditions lead to the worst-case time complexity in Quick Sort. Discuss common strategies to mitigate this (e.g., randomized pivot selection, median-of-three pivot).
6.  Is Quick Sort an in-place sorting algorithm? Is it a stable sorting algorithm? Explain.

**D. Binary Search**
1.  Explain the recursive Binary Search algorithm.
2.  Illustrate Binary Search with a suitable example.
3.  Write the algorithm for Binary Search.
4.  Prove that the worst-case time complexity of the Binary Search algorithm is O(log₂n) by deriving its recurrence relation.

---

**VII. Principles of Parallel Algorithm Design**

**A. Preliminaries - Decomposition, Tasks, and Dependency Graphs**
1.  Explain "data decomposition" in the context of parallel algorithms. What is its use?
2.  Explain partitioning of input data and partitioning of output data as part of data decomposition, using suitable examples.
3.  Explain "Tasks" and "Dependency Graphs" (also known as Task Interaction Graphs) in parallel algorithm design, providing examples.
4.  What is "Critical Path Length" in the context of a task dependency graph?

**B. Granularity, Concurrency, and Task-Interaction**
1.  Define and explain the term "Granularity" in parallel algorithm design.
2.  Define and explain "Degree of Concurrency" in parallel systems.

**C. Decomposition Techniques**
1.  Explain data decomposition techniques in detail with examples (this may overlap with VII.A.1 & VII.A.2 but is explicitly asked as a broader topic).
2.  What is "recursive decomposition"? Present it with an example.
3.  Write short notes on the following decomposition techniques:
    *   Exploratory decomposition
    *   Speculative decomposition

---

# Sample


**VII. Principles of Parallel Algorithm Design**

**A. Preliminaries - Decomposition**
1.  Define "decomposition" in the context of designing parallel algorithms. Explain why it is a fundamental initial step.
2.  Briefly describe the main types of decomposition: task decomposition and data decomposition. What is the primary focus of each?

**B. Tasks and Dependency Graphs**
1.  What constitutes a "task" in parallel computing?
2.  Explain what a task dependency graph is. How does it visually represent the execution order and dependencies among tasks in a parallel algorithm?
3.  Why is it important to identify and understand dependencies between tasks when designing parallel algorithms?

**C. Granularity**
1.  Define "granularity" as it relates to parallel algorithm design.
2.  Differentiate between fine-grained parallelism and coarse-grained parallelism. Discuss the potential advantages and disadvantages of each approach.
3.  How can the choice of granularity impact factors like communication overhead and load balancing in a parallel computing environment?

**D. Concurrency and Task-Interaction**
1.  Explain the concept of "concurrency" in the context of parallel algorithms and systems.
2.  Describe common patterns or types of task interaction that occur in parallel algorithms (e.g., data sharing, synchronization, communication).
3.  How can these task interaction patterns influence the overall performance, scalability, and complexity of a parallel algorithm?

**E. Decomposition Techniques**
1.  Describe the "domain decomposition" (also known as "data decomposition") technique for parallelizing algorithms. Provide a suitable example where this technique would be effective.
2.  Describe the "functional decomposition" (also known as "task decomposition") technique. Provide a suitable example where this technique would be applicable.
3.  Briefly mention "recursive decomposition" as a technique and how it relates to divide-and-conquer strategies in a parallel context.
4.  What key factors should a designer consider when selecting an appropriate decomposition technique for a given problem and target parallel architecture?

---
