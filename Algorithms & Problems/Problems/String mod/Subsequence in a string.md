# 392 Is Subsequence #26aug24
### Problem
```c
Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

Example 1:
Input: s = "abc", t = "ahbgdc"
Output: true

Example 2:
Input: s = "axc", t = "ahbgdc"
Output: false

Constraints:
    0 <= s.length <= 100
    0 <= t.length <= 104
    s and t consist only of lowercase English letters.
```
## Tips
```c
Its a very bad idea to use list[i] as a condition in while loop.
Better to use some arbitrary numbers comparision, but not 'value in list'

there are much simpler ways to move the pointer than messing(this time just slipped up on while loop condition)

for loop isnt needed if i can iterate carefully.
	Here for loop didnt end but while loop condition did, but i had not put a condition to exit when either of the list ended, but kept return only for the end of for loop.
```
## Code, Second version (simpler)
```python
def subsequence(s,t):

    if len(s) == 0:  # "" empty list to compare, True
        return True
    if len(t)==0:    # "" nothing to compare, False
        return False
    if len(s) == 1:  # one to compare, just linear search
        return(s[0] in t)

    i, j = 0, 0  # Two pointers for two lists

    while i < len(s) and j < len(t):  # if any list gets over, exit
        if s[i] == t[j]:   # if two are equal, move both pointers
            i += 1
            j += 1
        else:
            j +=1    # if not equal, move in the large list

    return ( i == len(s))   # if moved in s is == i, then all were present
```

## Code that worked (bit struggle in debugging)
```python
def subsequence(s,t):
    if len(s) == 0:
        return True
    elif len(t) == 0:
        return False
    elif len(s) == 1:
        return(s[0] in t)
        
    i, found = 0, 0  # Tracks matched letters
   
    for let in s:  # First loop iteration
        while i<len(t)-1 and t[i] != let:  # this was the mess
            i += 1

        if t[i] == let:
            found += 1
            i += 1
            
        if i >= len(t):  # had to exit before another loop
            return( found == len(s))  # otherwise IndexError
            
    return ( found == len(s))
```

### Debugging Taste cases
```c
s = "aaaaaa"
t = "bbaaaa"   # False
print(subsequence(s,t))

s = "acb"     # False
t = "ahbgdc"
print(subsequence(s,t))

s = "abc"
t = ""         # false
print(subsequence(s,t))

s = "abc"
t = "ahbgdc" # true
print(subsequence(s,t))

s = "axc"
t = "ahbgdc" # false
print(subsequence(s,t))

s = "xcadssfbsasd"
t = "xcabcddssfadbsfagshdj" # True
print(subsequence(s,t))

s = "axcadssfbsasd"
t = "xcabcddssfadbsfagshdj" # False
print(subsequence(s,t))
```


# 792 Number of matching subsequences #26aug24 
### Problem
```c
Given a string `s` and an array of strings `words`, return _the number of_ `words[i]` _that is a subsequence of_ `s`.

A **subsequence** of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

- For example, `"ace"` is a subsequence of `"abcde"`.

**Example 1:**

**Input:** s = "abcde", words = ["a","bb","acd","ace"]
**Output:** 3
**Explanation:** There are three strings in words that are a subsequence of s: "a", "acd", "ace".

**Example 2:**

**Input:** s = "dsahjpjauf", words = ["ahjpjau","ja","ahbwzgqnuk","tnmlanowax"]
**Output:** 2

**Constraints:**

- `1 <= s.length <= 5 * 104`
- `1 <= words.length <= 5000`
- `1 <= words[i].length <= 50`
- `s` and `words[i]` consist of only lowercase English letters.
```

## Solved 53 out of 54 cases (Using compression!!!, shouldn't have worked)
```python
def subsequence(s,words):

    def compress (chars):
        ss = []
        n = len(chars)
        poss_i = 0  # To iterate through the entire list
        write = 0   # To keep track of place to wrire results in list

        while poss_i < n:
            letter = chars[poss_i]
            lett_count = 0

            while poss_i < n and letter == chars[poss_i]:
                lett_count += 1
                poss_i += 1
  
            ss.append(letter)   
            write += 1

        return ("".join(ss))

    def is_substring(words, s):
        substring = 0
        checked = []
        for word in words:

            if word in checked:
                substring += 1
                continue

            if len(word) == 0:
                substring += 1
                continue

            if len(word) > len(s):
                continue

            i, j = 0, 0
            while i < len(word) and j < len(s):
  
                if word[i] == s[j]:
                    i += 1
                    j += 1
                else:
                    j += 1
  
            if len(word) == i:
                substring += 1
                checked.append(word)
  
        return(substring)

    if len(s) < 1000:
        return(is_substring(words,s))

    if len(s) > 1000:
        s = (compress(s))
        return(is_substring(words,s))


s = "abcde"
words = ["a","bb","acd","ace"] # 3
print(subsequence(s,words))

s = "dsahjpjauf"
words = ["ahjpjau","ja","ahbwzgqnuk","tnmlanowax"] # 2
print(subsequence(s,words))
```
## Worked but not mine
```python
class Solution:
    def numMatchingSubseq(self, s: str, words: List[str]) -> int:
        
        # Dictionary to store the indices of each character in `s`
        from collections import defaultdict
        import bisect
        
        char_positions = defaultdict(list)
        for index, char in enumerate(s):
            char_positions[char].append(index)
        
        def is_subsequence(word: str) -> bool:
            # Initialize the current position in `s` to -1
            current_position = -1
            for char in word:
                # If `char` is not in `s`, word cannot be a subsequence
                if char not in char_positions:
                    return False
                
                # Find the position of the next occurrence of `char` in `s`
                positions = char_positions[char]
                pos_index = bisect.bisect_right(positions, current_position)
                
                # If no valid position is found, `word` cannot be a subsequence
                if pos_index == len(positions):
                    return False
                
                # Update the current position to the position of `char`
                current_position = positions[pos_index]
            
            return True
        
        count = 0
        for word in words:
            if is_subsequence(word):
                count += 1
        
        return count
```