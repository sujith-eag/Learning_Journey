#23aug24 
# 345 Reversing the vowels in a string 
### Question
```c
Given a string s, reverse only all the vowels in the string and return it.
The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.
Example 1:
Input: s = "hello"
Output: "holle"

Example 2:
Input: s = "leetcode"
Output: "leotcede"
```
### Clue and Pseudocode
```c
# Version 1 (works, not space efficent)
> have list of vowels, (strings will work!!)
> make a list of given string,
> identify all vowels position and make list of vowels and their position
> reverse the list of indexes
> take first index position and first vowel and move it into list of strings in that position
> Join the list to make a string
```

```c
# two-pointer technique to scan and swap vowels, which avoids the need to use extra space for storing indices and vowels separately.

1. Initialization:
Two pointers, `l` (left) and `r` (right), to the start and end of the string.

2. Vowel Set: A string `v` to check for vowels.

3. Two-Pointer Technique:
    - Iterate while `l` is less than `r`.
    - If the character at position `l` is not a vowel, you move the left pointer `l` to the right.
    - elif the character at position `r` is not a vowel, you move the right pointer `r` to the left.
    - This iteration brings pointers to vowels, then the else is executed 
	- Both characters are vowels, swapped and then move both pointers inward.

4. Result Construction: After the loop completes, you convert the list `s` back to a string and return it.

# Advantages
- **Efficiency**: This method has a time complexity of O(n), where n is the length of the string, and it only uses a few additional variables, making it very space-efficient (O(1) space complexity aside from the input and output).

- **Simplicity**: The two-pointer technique is both easy to understand and implement.
```
## Code
### Final Code (More efficient without extra lists)
```python
class Solution:
    def reverseVowels(self, s: str) -> str:
        l, r = 0, len(s) - 1
        vowels = "aeiouAEIOU"
        s = list(s)
	        
        while l < r:
            if s[l] not in vowels:
                l += 1
            elif s[r] not in vowels:
                r -= 1
            else:
                s[l], s[r] = s[r], s[l]
                l += 1
                r -= 1
        
        return "".join(s)

solution = Solution()
result = solution.reverseVowels("hello")
print(result)  # Output should be "holle"
```
### Second version
```python
def reverseVowels( s: str) -> str:
    tester = ["a","A","e","E","i","I","o","O","U","u"]
    indexe = []
    vovels = []
    strlist = []

    for i in range(len(s)):
        strlist.append(s[i])
        if s[i] in tester:
            vovels.append(s[i])
            indexe.append(i)

    indexe.reverse()

    for pos in range(len(indexe)):
        strlist[indexe[pos]] = vovels[pos]
  
    return("".join(strlist))
    print(strlist)

s = "Hellow worldekjp Amn"
print(s)
print(reverseVowels(s))
```
### First version
```python
def reverseVowels( s: str) -> str:
    tester = ["a","A","e","E","i","I","o","O","U","u"]
    slist = list(s)    # list of original strings
    indexe = []  # index place of vowels
    vovels = []   # collection of all vowels

    for i in range(len(s)):
        if s[i] in tester:
            vovels.append(s[i])
            indexe.append(i)

    indexe.reverse()

    for pos in range(len(indexe)):
        a = vovels[pos]   # take 1st letter from vovels list
        b = indexe[pos]   # take 1st number from reversed indexe list
        slist[b] = a   # place vovels from opposite end  

    sreverse = "".join(slist)
    print(sreverse)

s = "Hellow worldekjp Amn"
print(s)
print(reverseVowels(s))
```