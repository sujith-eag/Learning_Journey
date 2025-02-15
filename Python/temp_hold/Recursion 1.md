
# Recursion

### Understanding Recursion:

1. **Base Case**:
   - This is the simplest form of the problem that can be solved directly without further recursion. It serves as the termination condition for the recursive process.

2. **Recursive Case**:
   - This is where the function calls itself with a smaller or simpler version of the original problem. Each recursive call reduces the original problem until it reaches the base case.

3. **Stack Usage**:
   - Recursion uses the system stack to manage function calls. Each recursive call pushes a new stack frame onto the call stack until the base case is reached. Then, it begins to pop these frames off the stack, resolving each function call sequentially.

### Example of Recursive Function (Factorial Calculation):

```python
def factorial(n):
    if n == 0:      # Base case
        return 1
    else:            # Recursive case
        return n * factorial(n - 1)
```

In this example:
- `factorial(5)` would compute as `5 * factorial(4)`, then `4 * factorial(3)`, and so on until `factorial(0)` is reached, which returns `1`.

### Other Ways of Achieving Recursion-like Behavior:

1. **Iteration (Looping)**:
   - Many recursive algorithms can be converted into iterative algorithms using loops. Iterative solutions often involve maintaining state variables to control the iteration and mimic the call stack behavior of recursion.

   Example of factorial calculation using iteration:

```python
def factorial(n):
   result = 1
   for i in range(1, n + 1):
	   result *= i
   return result
```
- - `for i in range(1, n + 1)`: This loop iterates over the integers from 1 to `n` inclusive (`n + 1` is used because the `range` function is exclusive of the upper limit).
- `result *= i`: In each iteration of the loop, `i` (which starts from 1 and goes up to `n`) is multiplied with `result`. This accumulates the factorial calculation.


2. **Using Data Structures (e.g., Stack)**:
   - Explicitly managing a stack data structure can simulate recursive function calls. This approach is useful when tail recursion optimization is not available in the programming language.

3. **Tail Recursion** (Optimization):
   - Some programming languages optimize tail-recursive functions to reuse the same stack frame for each recursive call, effectively converting recursion into an iterative process. Not all languages support this optimization.

### Pros and Cons of Recursion:

- **Pros**:
  - Simplifies complex problems by breaking them down into smaller, more manageable subproblems.
  - Can lead to elegant and concise code for certain types of problems.

- **Cons**:
  - Uses more memory due to the overhead of managing the call stack.
  - May lead to stack overflow errors if not managed carefully or if recursion depth is too deep.

### Choosing Between Recursion and Iteration:

- **Recursion**: Use when the problem can be naturally divided into smaller subproblems and when the base case is straightforward to define.
  
- **Iteration**: Prefer when efficiency and memory usage are critical, or when the problem is better suited to an iterative approach (e.g., simple loops).

In conclusion, recursion is a powerful technique in programming for solving problems by breaking them down into smaller instances of the same problem. It offers an alternative approach to iteration but requires careful consideration of stack usage and termination conditions to avoid potential pitfalls like stack overflow.


## Recursive Function
```python
def factorial (n):
    if n <= 0:
        return(1)
    else:
        val = n* factorial(n-1)
        return(val)

n! = n (n-1) (n-2)....1
n! = n (n-1)!            # this is what is being used
  

# EXAMPLES

def factors (n):         # to find factors of a number n
    factorslist = []
    for i in range (1,n+1):            
        if n%i == 0:
            factorslist.append(i)
    return(factorslist)

def isprime(n):   # To find if it is prime number - it has factors 1 and itself [1,n]
    return( factors(n) == [1,n] )       # factors of 17 is [1,17] ,  1 should not be reported as prime, factors(1) is [1], not [1,1]

def primesupto(n):         # Primes upto n
    primelist = []
    for i in range (1, n+1):
        if isprime(i):
            primelist = primelist + [i]
    return(primelist)

def nprimes(n):           # List the First n primes
    (count, i, plist) = (0, 1, [])       # here there is no way to fix how many repetition so while loop is used
    while count < n:
        if isprime(i):
            (count, plist) = (count+1, plist+[i])
        i = i+1
    return(plist)

a = 11
print(factors(a))
print(isprime(a))
print(primesupto(a))
print(nprimes(a))
```