
Consider a system with five processes P_0 through P_4 and three resource types ( A ), ( B ), and ( C ). Resource type ( A ) has 10 instances, ( B ) has 5 instances, and  C  has 8 instances. Suppose at time ( t_0 ), the following snapshot of the system has been taken:

| Processes | Allocation A | Allocation B | Allocation C | Max A | Max B | Max C | Available A | Available B | Available C |
| --------- | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----------- | ----------- | ----------- |
| P0        | 0            | 1            | 2            | 7     | 5     | 3     | 3           | 3           | 2           |
| P1        | 2            | 0            | 0            | 3     | 2     | 2     | -           | -           | -           |
| P2        | 3            | 0            | 1            | 9     | 0     | 2     | -           | -           | -           |
| P3        | 2            | 1            | 1            | 2     | 2     | 2     | -           | -           | -           |
| P4        | 0            | 0            | 2            | 4     | 3     | 3     | -           | -           | -           |

Answer the following questions using Banker’s Algorithm:
i) What will be the content of the Need matrix?
ii) If a request from process \( P_2 \) arrives for (2, 0, 1), can it be granted?

___

a. Consider the following snapshot of a system:  (10)

| Processes | Maximum R0 | Maximum R1 | Maximum R2 | Allocation R0 | Allocation R1 | Allocation R2 | Available R0 | Available R1 | Available R2 |
| --------- | ---------- | ---------- | ---------- | ------------- | ------------- | ------------- | ------------ | ------------ | ------------ |
| P0        | 4          | 1          | 2          | 1             | 0             | 2             | 2            | 2            | 0            |
| P1        | 1          | 5          | 1          | 0             | 3             | 1             | -            | -            | -            |
| P2        | 1          | 2          | 3          | 1             | 0             | 2             | -            | -            | -            |

Answer the following questions using Banker's Algorithm:
i) Is the system in a safe state?
ii) Will the system be able to satisfy a request by process P0 for one unit of resource type R1?
iii) Will the system be able to satisfy a request by process P1 for one unit of resource type R0?

___

a. Consider the following system state
There are three resources and three processes

| Processes | Maximum R1 | Maximum R2 | Maximum R3 | Allocation R1 | Allocation R2 | Allocation R3 | Available R1 | Available R2 | Available R3 |
| --------- | ---------- | ---------- | ---------- | ------------- | ------------- | ------------- | ------------ | ------------ | ------------ |
| P1        | 2          | 1          | 2          | 1             | 0             | 1             | 2            | 1            | 2            |
| P2        | 3          | 2          | 4          | 0             | 0             | 1             | -            | -            | -            |
| P3        | 4          | 2          | 1          | 1             | 1             | 1             | -            | -            | -            |

Answer following questions using Bankers algorithm.
i) Is the system in a safe state?
ii) Consider each of the following requests and say if it can be
granted. i. P3 requests 1 0 0 ii. P1 requests 0 1 0
iii) P2 requests 2 0 0 iv. P2 requests 1 0 1.

___

a. Considering a system with five processes P0 through P4 and three
resources types A, B, C. Resource type A has 10 instances, B has
5 instances and type C has 9 instances. Suppose at time t0 following
snapshot of the system has been taken:

| Processes | Allocation A | Allocation B | Allocation C | Max A | Max B | Max C | Available A | Available B | Available C |
| --------- | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----------- | ----------- | ----------- |
| P0        | 0            | 1            | 2            | 7     | 5     | 3     | 3           | 3           | 2           |
| P1        | 2            | 0            | 0            | 3     | 2     | 2     | -           | -           | -           |
| P2        | 3            | 0            | 2            | 9     | 0     | 2     | -           | -           | -           |
| P3        | 2            | 1            | 1            | 2     | 2     | 2     | -           | -           | -           |
| P4        | 0            | 0            | 2            | 4     | 3     | 3     | -           | -           | -           |

Answer the following questions using Banker’s algorithm:
i) What will be the content of the Need matrix?
ii) If a request from process P1 arrives for (1 0 2), can it be granted?

___

d. Consider the following snapshot of a system.

| Processes | Allocation A | Allocation B | Allocation C | Max A | Max B | Max C | Available A | Available B | Available C |
| --------- | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----------- | ----------- | ----------- |
| P0        | 0            | 1            | 0            | 7     | 5     | 3     | 3           | 3           | 2           |
| P1        | 2            | 0            | 0            | 3     | 2     | 2     | -           | -           | -           |
| P2        | 3            | 0            | 2            | 9     | 0     | 2     | -           | -           | -           |
| P3        | 2            | 1            | 1            | 2     | 2     | 2     | -           | -           | -           |
| P4        | 0            | 0            | 2            | 4     | 3     | 3     | -           | -           | -           |


Consider the a system with 5 processes P0 through P4 and 3 resource
types A,B,C. Resource type A has 10 instances, B has 5 instances and
C has 7 instances.
Answer the following questions using the Banker’s algorithm.
i) Find the content of the Need matrix?
ii) Judge the system is in Safe state?

___

c. Assume that there are 5 processes, P0 through P4, and 4 types of
resources. At time T0, the system state is as follows:

| Processes | Allocation A | Allocation B | Allocation C | Max A | Max B | Max C | Available A | Available B | Available C |
| --------- | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----------- | ----------- | ----------- |
| P0        | 5            | 2            | 3            | 3     | 1     | 2     | 1           | 2           | 2           |
| P1        | 4            | 6            | 2            | 3     | 4     | 1     | -           | -           | -           |
| P2        | 2            | 1            | 7            | 0     | 0     | 5     | -           | -           | -           |
| P3        | 6            | 3            | 1            | 5     | 1     | 0     | -           | -           | -           |
| P4        | 3            | 5            | 1            | 1     | 4     | 0     | -           | -           | -           |

Answer the following questions:
i) Construct the need matrix.
ii) Is the system in a safe state? If yes, what is the safe sequence?
iii) If a request for process p2 arrives for (1, 2, 0) can it be granted immediately.

____

a. Consider the following Snapshot of the system:

| Processes | Allocation A | Allocation B | Allocation C | Allocation D | Max A | Max B | Max C | Max D | Available A | Available B | Available C | Available D |
| --------- | ------------ | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----- | ----------- | ----------- | ----------- | ----------- |
| P0        | 0            | 1            | 2            | 0            | 1     | 5     | 2     | 0     | 1           | 2           | 1           | 5           |
| P1        | 1            | 0            | 0            | 1            | 7     | 5     | 3     | 0     | -           | -           | -           | -           |
| P2        | 1            | 3            | 5            | 2            | 3     | 4     | 2     | 3     | -           | -           | -           | -           |
| P3        | 0            | 1            | 4            | 0            | 6     | 5     | 6     | 5     | -           | -           | -           | -           |
| P4        | 0            | 1            | 4            | 6            | 5     | 6     | 5     | 6     | -           | -           | -           | -           |

Answer following questions using Bankers algorithm.
i) Is the system in a safe state?
ii) Can a request for (0, 4, 2, 0) by P1 be granted immediately?   Give reason.

___

a. (i) For the following snapshot find the safe sequence using Banker’s algorithm. The number of resource units are R1, R2, R3 which are 7, 7, 10 respectively.

| Process | Allocated A | Allocated B | Allocated C | Max A | Max B | Max C |
| ------- | ----------- | ----------- | ----------- | ----- | ----- | ----- |
| P1      | 2           | 2           | 3           | 3     | 6     | 8     |
| P2      | 2           | 0           | 3           | 4     | 3     | 3     |
| P3      | 1           | 2           | 4           | 3     | 4     | 4     |

___

a. Consider the Snapshot of the system:

| Process | Allocation A | Allocation B | Allocation C | Allocation D | Max A | Max B | Max C | Max D | Available A | Available B | Available C | Available D |
| ------- | ------------ | ------------ | ------------ | ------------ | ----- | ----- | ----- | ----- | ----------- | ----------- | ----------- | ----------- |
| P0      | 0            | 0            | 1            | 2            | 0     | 0     | 1     | 2     | 1           | 5           | 2           | 0           |
| P1      | 1            | 0            | 0            | 0            | 1     | 7     | 5     | 0     | -           | -           | -           | -           |
| P2      | 1            | 3            | 5            | 4            | 2     | 3     | 5     | 6     | -           | -           | -           | -           |
| P3      | 0            | 6            | 3            | 2            | 0     | 6     | 5     | 2     | -           | -           | -           | -           |
| P4      | 0            | 0            | 1            | 4            | 0     | 6     | 5     | 6     | -           | -           | -           | -           |


Answer the following questions using the banker’s algorithm:
(i)What is the content of the matrix Need?
(ii)Is the system in a safe state?
If a request from a process P1 arrives for (0, 4, 2, 0), can the request be granted immediately?


___