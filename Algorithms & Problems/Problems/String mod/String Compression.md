# 443 String Compression #25aug24 
## Problem
```c
Given an array of characters chars, compress it using the following algorithm:

Begin with an empty string s. For each group of consecutive repeating characters in chars: If the group length is 1, append the character to s.
Otherwise, append the character followed by the group length.

The compressed string 's' should not be returned separately, but instead, be stored in the input character array chars. 
Note that group lengths that are 10 or longer will be split into multiple characters in chars.

After you are done modifying the input array, return the new length of the array.
You must write an algorithm that uses only constant extra space.

Example 1:
Input: chars = ["a","a","b","b","c","c","c"]
Output: Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]
Explanation: The groups are "aa", "bb", and "ccc". This compresses to "a2b2c3".

Example 2:
Input: chars = ["a"]
Output: Return 1, and the first character of the input array should be: ["a"]
Explanation: The only group is "a", which remains uncompressed since it's a single character.

Example 3:
Input: chars = ["a","b","b","b","b","b","b","b","b","b","b","b","b"]
Output: Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].
Explanation: The groups are "a" and "bbbbbbbbbbbb". This compresses to "ab12".

Constraints:
    1 <= chars.length <= 2000
    chars[i] is a lowercase English letter, uppercase English letter, digit, or symbol.
```
## Tips
```c
Proper use of double while loop to select unique lettrs to count.
	one loop to select unique characters
	another to loop to count that char, update list, move pointer forward
a way to convert group count to str and update.
Updating the list in place with results.

a temporary character holder
A value to move through the list (for while loop and selecting next letter)
Having a resetting value to count num of similar letters
A number to keep track of where to insert the results

proper placement of each
```
## Code
```python
def compress (chars):
    n = len(chars)
    poss_i = 0  # To iterate through the entire list
    write = 0   # To keep track of place to wrire results in list

    while poss_i < n:
        letter = chars[poss_i]   # selecting first character
        lett_count = 0  # a value to count this perticular one, reset for next

        while poss_i < n and letter == chars[poss_i]:  # if next char, exit
            lett_count += 1   # counting the char
            poss_i += 1   # moving the counter

        chars[write] = letter   # updating list with character
        write += 1     # changing writing place
  
        if lett_count>1:   # updating number only if > 1
            for i in str(lett_count):   # invert to string and iterate
                chars[write] = i  # place in the list
                write += 1        # move write head to next place

    return write
# List is updated with result and total num of characters is returned
  
  

chars = ["a","a","b","b","c","c","c"]   # 6
print(compress(chars))
chars = ["a"]     # 1
print(compress(chars))
chars = ["a","b","b","b","b","b","b","b","b","b","b","b","b"]   # 4
print(compress(chars))
```

