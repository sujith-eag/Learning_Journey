# 344 Reversing a list of strings in place #23aug24 

## Damn it this is one line to reverse a list
```python
def stri(s):    
    lisp = s[::-1]
	return lisp

# anyway, the two pointer swap is important
# Works in VScode but not in Leetcode
```
### Clue
```c
> reversing a string in place needs swapping last and first
> swapping should happen simultaneously to avoid mistake
> running the number of swaps equal to len(list) will reverse string twice so comes back to the original state
> so in for loop the number can be half the len(list)
> in while loop we can use 2 pointers left and right which are moved to middle each run, stop when left and right swap.(left>right) or (left=right)
```
### Code
```python
# version 1 (for loop)
def stri(s):
    n = len(s)
 
    for i in range(n//2):
        (s[i], s[(n-1)-i]) = (s[(n-1)-i], s[i])
    return(s)
 
# version 2 (while loop) (Two pointer method)
def stri(s):
    n = len(s)
    left = 0
    right = n-1

    while left<right:
        (s[left], s[right]) = (s[right], s[left])
        left += 1
        right -= 1
    return(s)

s = ["h","e","l","l","o"]
print(stri(s))

s = ["H","a","n","n","a","h"]
print(stri(s))
```


# 151 Reverse Words in a string #23aug24 
### Question
```c
Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces. (there will be atleast one word in s)

Example 1:
Input: s = "the sky is blue"
Output: "blue is sky the"

Example 2:
Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.

Example 3:
Input: s = "a good   example"
Output: "example good a"

Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.
```

### Clue
```c
# my method
Use str.split() to make a list of string 
# didnt knew it automatically handles spaces and just gets words
Using while loop to itrate and remove all "" with  list.remove(")
reversing the words in list by 2 pointers
joining the words with " "

# But all it took was three lines							   
1.  Using `s.split()` without arguments automatically handles multiple spaces and trims leading and trailing spaces, so there's no need to manually remove empty strings.

2.  The `reverse()` method is used for reversing the list, which is simpler and more idiomatic than manually swapping elements.

3.  The `join()` method is used to concatenate the reversed list into a single string with a single space separator.
```
### Code
```python
def reverseWords(self, s: str) -> str:
    wordlist = s.split()
    wordlist.reverse()    
    return " ".join(wordlist)
```

```python
def reversewords(s):
    wordlist = s.split(" ")  # Split wherever " " is, even the trailing spaces
    
    while "" in wordlist:    # Iterate over the list of string words
        wordlist.remove("")  # remove all "", not " "

    n = len(wordlist)     # Double pointer method for swapping
    l, r = 0, n-1

    while l < r:        # stopping at mid point
        wordlist[l],wordlist[r] = wordlist[r],wordlist[l]
        l += 1
        r -= 1
        
    return(" ".join(wordlist))   # Join string with " "




s = "the sky is blue"
print(reversewords(s))

s = "  hello world  "
print(reversewords(s))
  
s = "a good        example"
print(reversewords(s))

s = "example"
print(reversewords(s))
```


# 186 Reverse words in a string II (paywall) #24aug24 
```c
Given a character array `s` that contains words separated by spaces, reverse the words in place. You need to modify the array in place without using extra space.

**Example:**
- Input: ["h", "e", "l", "l", "o", " ", "w", "o", "r", "l", "d"]
- Output: ["w", "o", "r", "l", "d", " ", "h", "e", "l", "l", "o"]
```
### Approach to Solve the Problem
```c
1. Reverse the Entire String of characters [::-1]:
   - Words are in the correct order, but characters within each word reversed.

2. Reverse Each Word Individually using - while end < len(list) :
   - Use two pointers to detect word by detecting spaces" "
   - Flip just that section
   - move the end pointer, move the beginning pointer to ends place

3. That last world:
   - When the loop ends, the pointer is at the end but loop doesnt run.
   - (even if made to run then a last letter doesnt get reversed because of split leaving out the last one).
   - So last switch is made outside the loop.
```

## Code
### Did better than GPT
```python
def revinplace(s):
    s = s[::-1]
    start,end = 0,0

    while end < len(s):
        if s[end] != " ":
            end += 1
            
        elif s[end] == " ":
            s[start:end] = s[start:end][::-1]
            end += 1
            start = end

    s[start:] = s[start:][::-1]
  # s[start:end] = s[start:end][::-1]   both work
  # Handling that last word, when loop ends with pointer at end
    return (s)
  
  
s = ["h","e","l","l","o"," ","w","o","r","l","d"," ","a","b","c","d"]
print(revinplace(s))

s = ["h", "e", "l", "l", "o", " ", "w", "o", "r", "l", "d"]
print(revinplace(s))
```
### Works but not clean and edge case handled sloppily 
```python
def revinplace(s):     # My way that worked but bit tricky indexing
    s = s[::-1]        # careful with len(l), -1, n-1, [start: ]
    start,end = 0,0    # also if, elif, condition sequence placement

    while end < len(s):
        if s[end] != " ":
            end += 1
# this is for the last one letter, when loop ends, can be moved out of loop
        if end == len(s):    
            s[start:] = s[start:][::-1]

        elif s[end] == " ":
            s[start:end] = s[start:end][::-1]
            end += 1
            start = end
            
    return(s)
```

### If in place sorting wasn't a thing ( crazy code )
```python
def revinplace1(s):
    s = "".join(s)
    s = s.split()
    s = s[::-1]
    s = " ".join(s)
    return(list(s))

def revinplace2(s):    # Hmm this is possible, dont try such experiments
    s = list(" ".join((("".join(s)).split())[::-1]))
    return(s)
```


# 557 Reverse words in a string III #24aug24 
```c
Given a string `s`, reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

**Example 1:**

**Input:** s = "Let's take LeetCode contest"
**Output:** "s'teL ekat edoCteeL tsetnoc"

**Example 2:**

**Input:** s = "Mr Ding"
**Output:** "rM gniD"

**Constraints:**

- `1 <= s.length <= 5 * 104`
- `s` contains printable **ASCII** characters.
- `s` does not contain any leading or trailing spaces.
- There is **at least one** word in `s`.
- All the words in `s` are separated by a single space.
```
### Tips
```c
# surprised that it worked
> instead of using list() to convert strings to individual characters
> Use s.split() to make list of individual words, spaces removed, like strip()
> Iterate over list with for loop to get elements
> convert each 'word' to a list, reverse it [::-1]
> "".join() it into string, and reassign it in its spot list[i]
> lastly " ".join.() the entire list to combine the words into sentence, space is needed
```

### Code
```python
def revstring(s):
    lisp = s.split()

    for i in range(len(lisp)):
        temp = list(lisp[i])[::-1]
        lisp[i] = "".join(temp)
    return(" ".join(lisp))  

#  for word in lisp:  cant do this as i is needed to put it back in the list

s = "Let's take LeetCode contest"
print(revstring(s))

s = "s'teL ekat edoCteeL tsetnoc"
print(revstring(s))

s = "Mr Ding"
print(revstring(s))
  
s = "rM gniD"
print(revstring(s))
```
