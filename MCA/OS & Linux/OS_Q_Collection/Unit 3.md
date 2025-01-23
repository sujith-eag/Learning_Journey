

_____
___


**5.**  
a) Consider the following snapshot of a system:

|Process|Allocation|Max|Available|
|---|---|---|---|
||A B C D|A B C D|A B C D|
|P0|0 0 1 2|0 0 1 2|1 5 2 0|
|P1|1 0 0 0|1 7 5 0||
|P2|1 3 5 4|2 3 5 6||
|P3|0 6 3 2|0 6 5 2||
|P4|0 0 1 4|0 6 5 6||

Answer the following questions using the Banker’s algorithm:  
i) What is the content of the matrix **Need**?  
ii) Is the system in a safe state?  
iii) If a request from process P1 arrives for (0, 4, 2, 0), can the request be granted immediately?

b) Explain the concept of segmentation. What are the advantages of segmentation?

**6.**  
a) Consider the reference string:  
`1, 2, 3, 4, 6, 5, 2, 5, 5, 6, 4, 1, 1, 2, 3, 4`  
with 4 memory frames. Determine the page faults using:  
i) FIFO  
ii) LRU  
iii) Optimal Page Replacement

b) What are the necessary conditions to form a deadlock? Explain techniques to prevent deadlock. Demonstrate how to identify deadlocks using a resource allocation graph.



**5.**  
a) For the following snapshot, find the safe sequence using Banker’s algorithm. The number of resource units is as follows: R1 = 7, R2 = 7, R3 = 10.

| Process | Allocated Resources | Maximum Requirements |
|---------|----------------------|----------------------|
| P1      | 2  2  3             | 3  6  8             |
| P2      | 2  0  3             | 4  3  3             |
| P3      | 1  2  4             | 3  4  4             |

b) Distinguish between:  
   i) Logical vs physical address space  
   ii) Paging vs segmentation  
   iii) First fit and best fit algorithms  

c) Given five memory partitions of 100 KB, 500 KB, 200 KB, 300 KB, and 600 KB (in order), determine how each of the first fit, best fit, and worst fit algorithms places processes of 212 KB, 417 KB, 112 KB, and 426 KB (in order). Which algorithm uses memory most efficiently?

**6.**  
a) Does deadlock exist if a cycle exists? Justify your answer with a suitable example.  
b) A small computer has 3 page frames. A process makes the following list of page references:  
   `5, 4, 3, 2, 1, 4, 3, 5, 4, 3, 2, 1, 5`  
   Determine the number of page faults using FIFO, LRU, and Optimal page replacement algorithms.



**5.**  
a) What is a deadlock? How do you recover the system from a deadlock?  
b) What is segmentation? Illustrate it with a neat diagram.  
c) Narrate the different components of a Resource Allocation Graph (RAG). How can RAG be analyzed with respect to safe and unsafe states?  

**6.**  
a) Under what circumstances do page faults occur? Describe the actions taken by the operating system when a page fault occurs.  
b) A process references 5 pages (A, B, C, D, E) in the following order:  
   `A, B, C, D, A, E, B, C, E, D`  

   Assuming the replacement algorithms are FIFO, LRU, and Optimal, find the number of page faults during the sequence of references, starting with an empty main memory with 3 frames.  

c) Briefly explain the structures of the following page tables:  
   i) Hierarchical Page Table  
   ii) Inverted Page Table  


**5.**  
a) Consider the following snapshot of a system:  

| Process | Allocation (A, B, C, D) | Maximum (A, B, C, D) | Available (A, B, C, D) |
|---------|--------------------------|-----------------------|-------------------------|
| P0      | 0, 0, 1, 2              | 0, 0, 1, 2           | 1, 5, 2, 0             |
| P1      | 1, 0, 0, 0              | 1, 7, 5, 0           |                         |
| P2      | 1, 3, 5, 4              | 2, 3, 5, 6           |                         |
| P3      | 0, 6, 3, 2              | 0, 6, 5, 2           |                         |
| P4      | 0, 0, 1, 4              | 0, 6, 5, 6           |                         |

Answer the following using the Banker’s algorithm:  
   i) Is the system in a safe state?  
   ii) Can the request for (0, 4, 2, 0) by P1 be granted immediately? Justify your answer.  

b) Discuss different ways of recovering from deadlocks.  
c) Explain, with the help of a neat diagram, how TLB can be used to improve effective access time.  

**6.**  
a) In a real computer system, neither the resources available nor the demands of processes for resources remain consistent over long periods. If deadlock is controlled by the Banker’s algorithm, analyze whether the following changes can be made safely, and under what circumstances:  
   i) Increase Available (new resources added)  
   ii) Decrease Available (resource permanently removed)  
   iii) Increase Max for one process (the process may need more resources)  
   iv) Decrease Max for one process (the process needs fewer resources)  
   v) Increase the number of processes  
   vi) Decrease the number of processes  

b) With a neat diagram, describe the paging process.  
c) Given the reference string `12, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5`, compare the number of page faults for LRU and Optimal page replacement algorithms using three frames.  



**5.**  
a) What are the necessary conditions for deadlock to occur? Differentiate between deadlock prevention and deadlock avoidance.  
b) With a neat diagram, explain the concept of segmentation. What are the advantages of segmentation?  

**6.**  
a) A computer has 4 page frames. A process makes the following list of page references:  
   `1, 2, 3, 4, 6, 3, 2, 1, 5, 2, 3, 1, 2, 5, 6`.  

   How many page faults occur using the following algorithms:  
   i) FIFO (initially 3 frames are filled)  
   ii) LRU (initially 2 frames are filled)  
   iii) Optimal Page Replacement (initially 1 frame is filled)  

b) With a neat diagram and example, demonstrate the working of paging hardware with TLB.  


**5.**  
a) What is a deadlock? What are the four necessary conditions for a deadlock to occur?  
b) Consider a system with processes P1, P2, P3, P4, and resources R1 and R2, where both resources have 2 instances. Analyze whether the system leads to a deadlock based on the given conditions.  
c) Assume there are 5 processes (P0 to P4) and 4 types of resources. At time T0, the system state is as follows:  

| Process | Max (A, B, C) | Allocation (A, B, C) | Available (A, B, C) |
|---------|---------------|-----------------------|---------------------|
| P0      | 5, 2, 3       | 3, 1, 2              | 1, 2, 2             |
| P1      | 4, 6, 2       | 3, 4, 1              |                     |
| P2      | 2, 1, 7       | 0, 0, 5              |                     |
| P3      | 6, 3, 1       | 5, 1, 0              |                     |
| P4      | 3, 5, 1       | 1, 4, 0              |                     |

Answer the following:  
i) Construct the Need matrix.  
ii) Is the system in a safe state? If yes, provide the safe sequence.  
iii) If a request for process P2 arrives for (1, 2, 0), can it be granted immediately?  

**6.**  
a) With a neat diagram, explain paging hardware with a Translation Lookaside Buffer (TLB).  
b) Consider the following page reference string:  
   `1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 1, 2, 3, 6`  

Calculate the number of page faults using the following algorithms with 3 and 4 frames:  
   i) FIFO  
   ii) LRU  
   iii) Optimal page replacement  



**5.**  
a) Elaborate on the system model to acquire required resources.  
b) Define the following terms:  
   i) Safe state  
   ii) Aborted state  
   iii) Claim edge  
   iv) Cycle state  

c) Propose methods to recover the system from a deadlock situation.  
d) Consider the following snapshot of a system:  

| Allocation |   | Max |   | Available |   |  
|------------|---|-----|---|-----------|---|  
| A  B  C    |   | A  B  C |   | A  B  C |   |  
| P0  0  1  0 |   | 7  5  3 |   | 3  3  2 |   |  
| P1  2  0  0 |   | 3  2  2 |   |         |   |  
| P2  3  0  2 |   | 9  0  2 |   |         |   |  
| P3  2  1  1 |   | 2  2  2 |   |         |   |  
| P4  0  0  2 |   | 4  3  3 |   |         |   |  

The system has 5 processes (P0 through P4) and 3 resource types (A, B, C).  
Resource A has 10 instances, B has 5 instances, and C has 7 instances.  
Answer the following using the Banker’s algorithm:  
i) Find the content of the Need matrix.  
ii) Determine if the system is in a safe state.  

**6.**  
a) Illustrate the following concepts:  
   i) Dynamic Loading  
   ii) Address Binding  
   iii) Swapping  

b) What is memory protection? Explain its importance with proper justifications.  
c) Consider the following page reference string:  
   `1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 3, 6`  

Find the number of page faults using the following algorithms (assume 3 frames):  
   i) FIFO  
   ii) LRU  
   iii) Optimal Replacement  



**5.**  
a) A process references 5 pages (A, B, C, D, E) in the following order:  
   `A, B, C, D, A, E, B, C, E, D`  
Assume the replacement algorithms are FIFO, LRU, and Optimal. Find the number of page faults during the sequence of references, starting with an empty main memory with 3 frames.  

b) Briefly explain the structures of the following page tables:  
   i) Hierarchical page table  
   ii) Inverted page table  

c) Under what circumstances do page faults occur? Describe the actions taken by the OS when a page fault occurs.  

**6.**  
a) What do you mean by deadlock? How can the system recover from a deadlock?  
b) Discuss the different components of a Resource Allocation Graph (RAG). Analyze the RAG with respect to safe and unsafe states.  
c) What is segmentation? Illustrate it with a neat sketch.  



**5.**  
a) Consider a system with five processes (P0 to P4) and three resource types (A, B, C).  
Resource instances:  
- A = 10, B = 5, C = 9  

At time \( t_0 \), the snapshot is as follows:  

| Process | Allocation (A, B, C) | Max (A, B, C) | Available (A, B, C) |
|---------|-----------------------|---------------|----------------------|
| P0      | 0, 1, 2              | 7, 5, 3       | 3, 3, 2             |
| P1      | 2, 0, 0              | 3, 2, 2       |                      |
| P2      | 3, 0, 2              | 9, 0, 2       |                      |
| P3      | 2, 1, 1              | 2, 2, 2       |                      |
| P4      | 0, 0, 2              | 4, 3, 3       |                      |

i. What is the content of the Need matrix?  
ii. If a request from process P1 arrives for \( (1, 0, 2) \), can it be granted?  

b) Demonstrate how to identify deadlocks using a Resource Allocation Graph (RAG).  

**6.**  
a) What are the necessary conditions for deadlock formation? Explain.  
b) Write the deadlock detection algorithm.  



### **5.**  
a) Consider the following system state:  

| Processes | Maximum (R1, R2, R3) | Current Allocation (R1, R2, R3) | Available (R1, R2, R3) |
| --------- | -------------------- | ------------------------------- | ---------------------- |
| P1        | 2, 1, 2              | 1, 0, 1                         | 2, 1, 2                |
| P2        | 3, 2, 4              | 0, 0, 1                         |                        |
| P3        | 4, 2, 1              | 1, 1, 1                         |                        |

Answer the following questions using the Banker's Algorithm:  
i) Is the system in a safe state?  
ii) Consider the following requests and state whether they can be granted:  
   - P3 requests (1, 0, 0)  
   - P1 requests (0, 1, 0)  
   - P2 requests (2, 0, 0)  
   - P2 requests (1, 0, 1)  

b) With a neat diagram of paging hardware, explain the concept of paging. How does paging differ from segmentation? Explain with an example.  

---

### **6.**  
a) What are the different ways a deadlock can be handled? Discuss different ways of recovering from deadlocks.  
b) Given the page reference string:  
   \( 1, 2, 3, 4, 2, 1, 5, 6, 2, 1, 2, 3, 7, 6, 3, 2, 1, 2, 3, 6 \)  
   And 3 frames:  
   Compare the number of page faults for LRU, FIFO, and Optimal page replacement algorithms.  
c) Write a note on thrashing.  


**5.**  
a) What is a deadlock? Explain the Readers-Writers Problem with code snippets and explain how the deadlock is avoided in the scenario.  
b) Illustrate any two page-replacement algorithms for the following reference string:  
   \( 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5 \)  

**6.**  
a) Exemplify the process of paging and segmentation of memory.  
b) Explain the dining philosophers problem with code snippets and explain how the deadlock situation is avoided in the problem.  
