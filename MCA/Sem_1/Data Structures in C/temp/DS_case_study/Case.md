
### **Case Study Report Format: Problem-Based (10 Marks)**

1. **Introduction (2M)**
    - Clearly state and summarize the focus of the case study.
    - Summarize the key observations and findings.
    
2. **Background (2M)**
    - Provide relevant facts and context.
    - Include necessary background information.
    
3. **Proposed Solutions (2M)**
    - Suggest practical and feasible solutions that exist or ways to enhance the situation as it is.
    - Explain how these solutions can address the identified problems.
    
4. **Implementation (3M)**
    - Outline the steps required to execute the proposed solutions.
    - Provide a structured approach for implementation.

5. **Conclusion (1M)**
    - Summarize key insights from the case study.
    - Highlight the impact of the proposed solutions.

____

Asynchronous cryptography / Public key cryptography

Key pairs of a person
Public key of a person is used to encrypt the message sent to a person(Mostly a lock handed out to lock the message), can be accessed only by decrypting it with that persons private key. 

248 bits. encryption size which can be the size of the file that can be encrypted.

Trap door approach of allowing one way of motion easily but not being able to return in the other direction to the starting point.

RSA is used to encrypt AES Key which is used to encrypt the body of the message since it has no limit on how much it can encrypt.

Prime number multiplication - results can be devided evenly by those two prime numbers , brute force is dividing by all primes.

Certificates



___

Cryptography Through Graph Structures: A Study of RSA and ECC

### **Case Study: Graph-Based Approaches to Secure Encryption – A Comparative Analysis of RSA and Elliptic Curve Cryptography (ECC)**

#### **📌 Objective:**

This case study explores the role of **graph theory in encryption**, focusing on two widely used cryptographic systems:

6. **RSA Encryption**, which relies on **graph-based prime factorization** and the difficulty of breaking large numbers into primes.
7. **Elliptic Curve Cryptography (ECC)**, which is based on **cyclic group graphs** formed by points on an elliptic curve.

We analyze how **graph traversal, number theory, and quantum computing** influence these encryption techniques and their future significance.

---

## **🔹 Introduction: The Need for Secure Encryption**

With the rise of **cybersecurity threats, quantum computing, and evolving cryptographic attacks**, modern encryption relies on **complex mathematical structures** to ensure security.

- Traditional encryption like **RSA** is based on **prime factorization**, which is computationally expensive but widely used.
- Modern encryption like **ECC** offers better security with **smaller key sizes**, leveraging **graph-based cyclic groups**.
- The **emergence of quantum computing** raises concerns about **breaking RSA via Shor’s Algorithm**, highlighting the need for quantum-resistant encryption.

This study compares the **graph-based foundations** of these cryptographic methods, evaluating their efficiency, security, and future implications.

---

## **🔹 The Role of Graph Theory in Cryptography**

Graph theory plays a key role in encryption due to the **complexity of number theory problems**:

- **Directed Graphs (DAGs)** represent **key exchange operations** in **Diffie-Hellman and ECC**.
- **Factorization Graphs** define the security of **RSA**, where **prime numbers form distinct nodes**.
- **Graph Traversal Problems** (Discrete Logarithm & Factoring) define the **hardness of breaking encryption**.
- **Quantum Graphs** (Shor’s Algorithm) provide **a polynomial-time solution to RSA’s security problem**.

These concepts help us evaluate **the efficiency and security of RSA vs ECC**.

---

## **🔹 Section 1: Diffie-Hellman & ECC – Secure Key Exchange as a Graph Problem**

### **1.1 Diffie-Hellman Key Exchange & Graph Traversal**

**Diffie-Hellman (DH) key exchange** is a fundamental method of securely exchanging cryptographic keys.

- **Mathematical Basis:** The **Discrete Logarithm Problem (DLP)**
- **Graph Representation:**
    - **Nodes:** Represent powers of a base generator `g` in modular arithmetic.
    - **Edges:** Represent exponentiation, forming a **directed cyclic graph**.

#### **Graph Theory Connection:**

- Computing `x` in **g^x mod p = y** is equivalent to **finding a path in a graph**.
- A brute-force attack is **equivalent to traversing all nodes**, making it computationally expensive.

---

### **1.2 Elliptic Curve Cryptography (ECC) – Cyclic Graphs in Encryption**

ECC operates on **points on an elliptic curve**, where encryption relies on the **Elliptic Curve Discrete Logarithm Problem (ECDLP)**.

- **Mathematical Basis:** `P + P + ... + P = kP`, where `P` is a point on the curve.
- **Graph Representation:**
    - **Nodes:** Represent **points on an elliptic curve**.
    - **Edges:** Represent **point addition operations**, forming a **cyclic graph**.

#### **Graph Theory Connection:**

- Computing `k` in `P = kG` is **equivalent to finding a cycle in a graph**.
- **Quantum attacks on ECC** require more **computational power than on RSA**, making ECC more secure against future threats.

---

## **🔹 Section 2: RSA Encryption & Its Dependence on Graph-Based Factorization**

### **2.1 Why Is Factoring Large Numbers Difficult? (Graph Theory Approach)**

RSA encryption relies on the fact that **factoring large numbers is hard**.

- **Mathematical Basis:** RSA is based on the difficulty of factoring `N = p * q`.
- **Graph Representation:**
    - **Nodes:** Represent prime factors.
    - **Edges:** Represent multiplication relationships between primes.

#### **Graph Theory Connection:**

- The **Factorization Graph** of `N` is **highly connected**, meaning **brute-force factorization is infeasible**.
- **Pollard’s Rho Algorithm** and **General Number Field Sieve (GNFS)** traverse this graph to find factors.

---

### **2.2 How Shor’s Algorithm Breaks RSA Using Quantum Graphs**

Shor’s Algorithm uses **quantum computing** to efficiently **traverse the factorization graph**.

- **Graph Representation:**
    - Uses **Quantum Fourier Transform (QFT)** to find cycles in a modular exponentiation graph.
- **Impact on RSA:**
    - Reduces factorization time from **exponential (classical computers) to polynomial (quantum computers)**.
    - **RSA keys are no longer secure in a post-quantum world**.

#### **Why ECC Is More Quantum-Resistant?**

- Shor’s Algorithm is **less effective against ECC** due to the **complex cyclic graph structure** of elliptic curves.

---

## **🔹 Section 3: Comparison of RSA vs ECC – Graph Complexity & Security**

|**Feature**|**RSA (Prime Factorization Graphs)**|**ECC (Cyclic Graphs on Elliptic Curves)**|
|---|---|---|
|**Graph Type**|Factorization Graph|Cyclic Graph|
|**Mathematical Hardness**|Factoring `N = p * q`|Solving `kP = P`|
|**Key Size for Equivalent Security**|2048-bit RSA = 256-bit ECC|ECC requires **smaller keys**|
|**Quantum Vulnerability**|Broken by **Shor’s Algorithm**|More **resistant** to quantum attacks|
|**Performance**|**Slower encryption & decryption**|**Faster with smaller keys**|

✅ **Future Significance:** ECC is becoming the **new standard** for encryption in **blockchain, IoT, and secure communications**.

---

## **🔹 Conclusion: The Future of Graph-Based Encryption**

8. **RSA vs ECC:**
    - **RSA relies on factorization graphs, which quantum computers can break.**
    - **ECC relies on cyclic group graphs, which offer stronger security with smaller key sizes.**
9. **Quantum Threats:**
    - **Shor’s Algorithm can efficiently traverse factorization graphs, breaking RSA.**
    - **ECC is currently more quantum-resistant but still requires future research.**
10. **Post-Quantum Cryptography:**
    - **Lattice-based cryptography** is emerging as a new alternative.
    - **Graph-based encryption schemes (like Zero-Knowledge Proofs) are being explored.**

### **Final Thought:**

**The future of cryptography depends on graph-based problems. Understanding these graph structures helps build more secure encryption for the post-quantum era.**

---

## **🔹 Key Takeaways**

|**Topic**|**Key Graph Concept**|**Significance**|
|---|---|---|
|**Diffie-Hellman Key Exchange**|**Discrete Logarithm Graph**|Secure **key exchange** in TLS, VPNs|
|**Elliptic Curve Cryptography**|**Cyclic Graphs**|Faster, **quantum-resistant encryption**|
|**RSA Factorization**|**Prime Factorization Graphs**|Basis of **modern public-key cryptography**|
|**Shor’s Algorithm**|**Quantum Graph Traversal**|Breaks **RSA using quantum computers**|

___

Let's break down exactly **how graph structures are involved** in **RSA** and **Elliptic Curve Cryptography (ECC)** and why graph **data structures** are relevant in cryptography.

---

## **🔹 Where Do Graph Structures Appear in RSA and ECC?**

Encryption schemes like **RSA and ECC** rely on **hard mathematical problems** that can be represented as **graphs**. These graph structures determine **how difficult it is to break the encryption** and **how efficiently encryption operates**.

---

## **1️⃣ Graph Structures in RSA – Prime Factorization Graphs**

### **🔹 How RSA Works:**

- RSA encryption is based on the **difficulty of factoring large numbers** into primes.
- If you **multiply two large prime numbers `p` and `q`**, the result `N = p × q` is **easy to compute**.
- However, **finding `p` and `q` from `N`** (factoring) is extremely difficult for large numbers.

### **🔹 Graph Representation of RSA:**

RSA factorization can be visualized as a **graph traversal problem**, where:

- **Nodes (Vertices):** Represent numbers, including `N`, its prime factors, and divisors.
- **Edges:** Represent **factorization relationships** between numbers.

#### **Example: Prime Factorization as a Graph**

For `N = 2310`, the factorization graph is:

```
        2310
       /    \
     77      30
    /  \    /  \
   7   11  5   6
            /  \
           2    3
```

- Each **number is a node**, and **edges represent division**.
- **Finding prime factors is equivalent to traversing this graph**.
- Large numbers create a **massive graph**, making traversal (factoring) computationally hard.

#### **Graph-Based Attacks on RSA**

- **Graph traversal algorithms** like **Pollard’s Rho** and **GNFS (General Number Field Sieve)** attempt to **break RSA encryption** by efficiently traversing the factorization graph.
- **Shor’s Algorithm (Quantum Computing)** uses **graph-based quantum Fourier transforms** to break RSA **exponentially faster**.

✅ **Why Graph Data Structures Matter in RSA?**

- **RSA security is based on the complexity of navigating the factorization graph**.
- **Graph algorithms help improve or attack RSA encryption**.

---

## **2️⃣ Graph Structures in ECC – Cyclic Groups of Points**

### **🔹 How ECC Works:**

- Instead of numbers, ECC operates on **points on an elliptic curve** defined by: y2=x3+ax+by^2 = x^3 + ax + b
- The core operation is **point addition**, where adding two points `P` and `Q` on the curve gives another point `R`.
- ECC encryption is based on the **Elliptic Curve Discrete Logarithm Problem (ECDLP)**:  
    **Given `G` and `Q = kG`, finding `k` is extremely hard**.

### **🔹 Graph Representation of ECC:**

ECC encryption **forms a cyclic graph structure**:

- **Nodes (Vertices):** Represent **valid points** on the elliptic curve.
- **Edges:** Represent **point addition operations** (`P + Q = R`).

#### **Example: Cyclic Graph of ECC Points**

For a **small** elliptic curve, the graph might look like:

```
   P1 → P2 → P3 → P4 → ... → Pn → P1  (Cycle)
```

- This **cyclic graph** represents **point addition operations**.
- Breaking ECC requires **traversing this graph backwards** (which is hard).

#### **Graph-Based Attacks on ECC**

- **Baby-step Giant-step Algorithm**: Uses **graph traversal techniques** to solve `k` in `Q = kG`.
- **Quantum Attacks**: Shor’s Algorithm **also applies to ECC**, but ECC is harder to break than RSA due to its **graph complexity**.

✅ **Why Graph Data Structures Matter in ECC?**

- ECC operates on a **cyclic graph** of points.
- **Graph-based problems make breaking ECC computationally expensive**.

---

## **3️⃣ RSA vs. ECC: Graph Complexity Comparison**

|**Aspect**|**RSA (Prime Factorization Graphs)**|**ECC (Cyclic Graphs)**|
|---|---|---|
|**Graph Type**|**Factorization Graph**|**Cyclic Graph**|
|**Encryption Basis**|Factoring `N = p * q`|Computing `k` in `Q = kG`|
|**Graph Traversal Problem**|**Finding prime factors is a path search problem**|**Finding `k` is a graph cycle problem**|
|**Quantum Vulnerability**|**Easily broken by Shor’s Algorithm**|**Harder to break due to complex graph cycles**|

---

## **🔹 Final Answer: Where Are Graph Data Structures Used in RSA and ECC?**

11. **RSA uses a factorization graph** where **nodes represent numbers** and **edges represent division relationships**.
12. **ECC uses a cyclic graph** where **nodes are elliptic curve points**, and **edges represent point addition operations**.
13. **Both encryption methods rely on graph traversal problems**, making **graph theory essential for cryptographic security**.

---
