#21aug24 

# 1768 Alternating Character Merge  

### Question

```c
You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`.
If a string is longer than the other, append the additional letters onto the end of the merged string. Return _the merged string._

**Example 1:**
**Input:** word1 = "abc", word2 = "pqr"
**Output:** "apbqcr"
**Explanation:** The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r

**Example 2:**
**Input:** word1 = "ab", word2 = "pqrs"
**Output:** "apbqrs"
**Explanation:** Notice that as word2 is longer, "rs" is appended to the end.
word1:  a   b 
word2:    p   q   r   s
merged: a p b q   r   s

**Example 3:**
**Input:** word1 = "abcd", word2 = "pq"
**Output:** "apbqcd"
**Explanation:** Notice that as word1 is longer, "cd" is appended to the end.
word1:  a   b   c   d
word2:    p   q 
merged: a p b q c   d
```
### Tip
```c
> Need to build a new string iteratively but simultaneously so one word from each are added side by side.
> Use the max length out of two for iteration
> when i from iterator becomes larger than len of a string, stop adding(to prevent error of OutboundIndex),  the longer string can continue

> += can be used to add a bit of string to another
> merged = merged + word[i]    long form
> merged += word[i]  short form 

> A def can be inside a def, nested functions so less self. to worry about
```

### Solution

```python
def mergeAlternately(word1: str, word2: str) -> str:
    (n, m) = (len(word1), len(word2))
    merged = ""

    for i in range(max(n, m)):
        if i < n:
            merged += word1[i]
        if i < m:
            merged += word2[i]
    return merged
    
result = mergeAlternately("weert", "asd")
print(result)
```

```python
# Struggling not knowing what to do with class
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        n = len(word1)
        m = len(word2)
        merged = ""

        for i in range(max(n, m)):
            if i < n:
                merged += word1[i]
            if i < m:
                merged += word2[i]
        return merged

solution = Solution()  # Create an instance of Solution

# Call the mergeAlternately method with test strings
result = solution.mergeAlternately("weert", "asd")

print(result)  # Print the result
# Expected Output: "waseertd"
```
#### One where list is used to store characters
```
# needs work
def listof(word1, word2):
    list1 = list(word1+word2)
    stri = ''.join(list1)
    return(stri)
  
print(listof(  "asdf ", "cvbnm "))

# asdf cvbnm
```
