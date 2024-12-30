
A **regular expression (regex)** is a string that defines a search pattern. 
It consists of a combination of **literal characters** and **meta-characters**. The meta-characters modify the literal characters to introduce flexibility and variability in pattern matching.

regex can **match more than just a literal string**. It can match a wide range of text patterns, allowing for flexible search, validation, and manipulation of strings. 
Regular expressions are commonly used to search for strings that follow a **pattern of interest**.

`"aeiou"` will match **exactly** the string `"aeiou"`. It does not allow for any variation.
`"[aeiou]{5}"` will match any string that consists of **five consecutive vowels** (in lowercase). characters must appear consecutively. It will match strings like `"aeiou"`, `"aaaee"`, but not `"abcde"`.


***Wildcards and Regex:***
While wildcards, such as `*` or `?`, can be used to express basic patterns, regex provides a more powerful and flexible mechanism for creating complex search patterns like,
- Matching sequences of characters.
- Requiring specific numbers of characters.
- Allowing optional characters.


___
### Metacharacters in Regex

The **regex** used in Linux was adopted from **POSIX** (Portable Operating System Interface for Unix), a series of standards that OS developers followed to ensure Unix and Unix-like systems shared features.

The original metacharacters described by POSIX form the **Basic Regular Expression** (BRE) set. Later, POSIX introduced the **Extended Regular Expression** (ERE) set, which uses the same metacharacters but with some differences, such as not requiring the backslash (`\`) for certain characters.

In regex, **brackets** (`[]`) are used to define a set of possible characters that can be matched. These brackets allow for more flexible and complex pattern matching.
- `[aeiou]` : Matches **any lowercase vowel**. It will match `a`, `e`, `i`, `o`, or `u`.
- `[a-e]`: Matches any of the characters from **a to e**. This includes `a`, `b`, `c`, `d`, and `e`.
- `[[:lower:]]` : This is an example of a **POSIX character class** within brackets. It matches any **lowercase letter** (equivalent to `[a-z]`).


---

### **POSIX Metacharacters in Regular Expressions:**

- **`^`**: Anchors the match to the **beginning** of the string.
    `^cat` matches "cat" only if it appears at the start of the string.

- **`$`**: Anchors the match to the **end** of the string.
    `cat$` matches "cat" only if it appears at the end of the string.

- **`*`**: Matches **0 or more** occurrences of the preceding element.
    `a*` matches "a", "aa", "aaa", or even an empty string.

- **`+`**: Matches **1 or more** occurrences of the preceding element.
    `a+` matches "a", "aa", "aaa", but **not** an empty string.

- **`?`**: Matches **0 or 1** occurrence of the preceding element.
    `a?` matches "" (empty string) or "a".

- **`.`**: Matches any **single character** (except newline).
    `a.b` matches "aab", "acb", "a1b", but **not** "ab" (missing character between "a" and "b").

- **`[]`**: Character class; matches any **one of the characters inside the brackets**.
    `[aeiou]` matches any vowel (e.g., "a", "e", "i", etc.).

- **`|`**: **Alternation**; matches either the pattern on the left or right.
    `cat|dog` matches either "cat" or "dog".

- **`()**`: **Grouping**; groups part of a regular expression.
    `(abc)+` matches "abc" repeated one or more times, e.g., "abc", "abcabc", etc.

- **`\`**: **Escape character**; used to escape special characters.
    `\.` matches a literal dot ".", and `\$` matches a literal dollar sign "$".

- **`{m}`**: Matches **exactly m occurrences** of the preceding element.
    `a{3}` matches exactly "aaa".

- **`{m,n}`**: Matches between **m and n occurrences** of the preceding element.
    `a{3,5}` matches "aaa", "aaaa", or "aaaaa".

- **`?`** (as non-greedy): Makes the preceding character **optional** or **non-greedy**.
    `a+?` matches the smallest possible match, i.e., it will match "a" rather than "aaa".


     
____
     

- **`\b`**: **Word boundary**.
    `\bcat\b` matches "cat" only if it appears as a whole word, not as part of a larger word like "catalog".

- **`\B`**: **Non-word boundary**.
    `\Bcat\B` matches "cat" if it is **not** at the start or end of a word (e.g., "scatalog").

- **`\d`**: Matches any **digit** (equivalent to `[0-9]`).
    `\d+` matches one or more digits, such as "123" or "42".

- **`\D`**: Matches any **non-digit** character.
    `\D+` matches one or more non-digit characters, such as "abc" or "!@#".

- **`\w`**: Matches any **word character** (letters, digits, and underscore, equivalent to `[a-zA-Z0-9_]`).
    `\w+` matches a sequence of word characters, such as "abc123" or "_username".

- **`\W`**: Matches any **non-word character**.
    `\W+` matches a sequence of non-word characters, such as `!!`, `@#$`, etc.

- **`\s`**: Matches any **whitespace character** (space, tab, newline).
    `\s+` matches one or more whitespace characters, such as spaces or tabs.

- **`\S`**: Matches any **non-whitespace** character.
    `\S+` matches a sequence of non-whitespace characters, such as "abc123" or "_hello".

		
---
			
### **POSIX Character Classes:**

- **`[:alnum:]`**: Matches any **alphanumeric** character (letters in any case and digits, equivalent to `[a-zA-Z0-9]`).   
	`[[:alnum:]]` matches "a", "1", "X", "b2", etc.    
	
- **`[:alpha:]`**: Matches any **alphabetic** character (letters, equivalent to `[a-zA-Z]`).
    `[[:alpha:]]` matches "a", "b", "Z", "X", but **not** digits or symbols.

- **`[:blank:]`**: Matches a **space or tab** character (`[ \t]`).
    `[[:blank:]]` matches spaces and tabs.

- **`[:cntrl:]`**: Matches any **control character** (ASCII 0–31).
    `[[:cntrl:]]` matches control characters like `^C`, `^D`, etc.

- **`[:digit:]`**: Matches any **digit** (equivalent to `[0-9]`).
    `[[:digit:]]` matches "0", "5", "9", etc.

- **`[:graph:]`**: Matches any **printable character excluding space** (e.g., `a`, `A`, `1`, etc.).
    `[[:graph:]]` matches "a", "A", "!", "1", but **not** space.

- **`[:lower:]`**: Matches any **lowercase letter** (equivalent to `[a-z]`).
    `[[:lower:]]` matches "a", "b", "z", etc.

- **`[:print:]`**: Matches any **printable character**, including space (equivalent to `[[:graph:] ]`).
    `[[:print:]]` matches "a", "1", " ", but **not** control characters.

- **`[:punct:]`**: Matches any **punctuation** character (e.g., `.`, `!`, `?`, `;`, etc.).
    `[[:punct:]]` matches ".", "!", "?", ";", etc.

- **`[:space:]`**: Matches any **whitespace** character (space, tab, newline, carriage return, etc.).
	`[[:space:]]` matches " ", "\t", "\n", etc.

- **`[:upper:]`**: Matches any **uppercase letter** (equivalent to `[A-Z]`).
	`[[:upper:]]` matches "A", "B", "Z", etc.

- **`[:xdigit:]`**: Matches any **hexadecimal digit** (equivalent to `[0-9a-fA-F]`).
    `[[:xdigit:]]` matches "1", "a", "F", "9", etc.

---

`^[[:alpha:]]+$` : This will match strings that consist only of alphabetic characters (both lowercase and uppercase).

`[[:digit:]]{3,5}` : This will match 3 to 5 consecutive digits.



___
____


### **Controlling Repeated Characters Through `*`, `+`, `?`**

These are used to express a variable number of times that `preceding character` in regex can appear in the string.

`*`: The preceding character can appear **0 or more times**.
    `1*0*` matches `11111000000`, `111111110`, `10`, `0`, or even an **empty string**.

   
`+` : The preceding character can appear **1 or more times**.
    `1+0+` matches `111110000`, `1111110`, `10`  
    but **not** `0`, `1111`, or an **empty string**.


`?` : The preceding character can appear **0 or 1 time**.
    `1?0?` matches `1`, `0`, `10`, or an **empty string**.

___

`a*b*c*` : Matches `aaaaabbbc`, `abc`, `ab`, `bbbbb`, or even **empty string**. (will match `abacab)
`a+b+c+` : Matches `aaaaabbbc`, `abc`, `abbbbbc`, but **not** an empty string or `1111`.
`a?b?c?` : Matches `abc`, `ab`, or **empty string**.
None will match with `abaaabc`as the letters are not in correct sequence.


**Literal Characters:** A regex can contain literal characters without the metacharacters modifying them.
`jpe?g` : Matches `jpeg` or `jpg` (with `e` being optional and `j,p, g` a must).
`hello!?` : Matches `hello` or `hello!` (with `!` being optional).


___

### **Using `.` (Dot)**

**`.`** matches any single character except a newline.   

`b.t` will match any string that has `b` followed by **any one character**, followed by `t`.
- It will match: `bat`, `bbt`, `b0t`, `b#t`, `b t`
- It will **not** match: `bt` (missing the middle character)
- `batt` (too many characters)


**`...`** (three dots) will match any three characters, including three blank spaces.



**Combining with Other Metacharacters** like `*`, `+`, and `?` can modify `.` to allow for more flexible matches:

**`.*`**: Matches any sequence of characters (including zero characters). `b.?t` means `b` followed by zero or one character of any kind followed by a `t`.
    `b.*t` will match: `bat`, `bbt`, `b0t`, `b#t`, `b t`, `bt`, `batt`, `b t`

**`.+`**: Matches any sequence of **one or more characters**.
    `b.+t` will match: `bat`, `bbbbbbt`, `b t`, `b?!!#&*t`, `bait`, `b00t`
     It will **not** match:  `bt` (since there must be at least one character between `b` and `t`)

**`.?`**: Matches zero or one character of any kind.
	`b.?t` will match: `bt`, `bat`, `b?t`, `b#t`, etc.


---


### Controlling Where a Pattern Matches

A regular expression need not match the full string, it can match **any substring** within a string, which is a contiguous sequence of characters found within the larger string.
- `a*b*c*` will match `abacab` because it looks for **zero or more occurrences** of `a`, `b`, and `c` in any order.
- `b.t` will match `batt` as it matches `b`, any character (represented by `.`), and `t`. It will also match strings like `bbbbbatttt` because it matches the substring "bat".
- `b?.t` and `b?.t+` will also match substrings within `bbbbbatttt`.

regex patterns like `a*`, `char*`, or `a*b*` can be too broad, matching anything and everything, becoming useless. 
To control where the regex matches, we can use anchors to enforce specific positions in the string.

*  **`^`** : Asserts the beginning of a string.
*  **`$`** : Asserts the end of a string.
*  **`^ and $`** : Asserts the start and end of the string, ensuring the entire string must match the pattern.

---

**`^b?.t`**:
- Will **not** match `bbbbbbatttt` because the pattern starts at the beginning of the string, where it expects an optional `b` (`b?`), followed by any character (`.`), and then `t`. However, the sequence does not match at the start.
- `b?` matches the first `b`, the `.` marks the second `b` but the `t+` does not match as the next character is not `t`.


**`^b?.t+`**:
- This will **not** match `bbbbbbatttt` either because it starts with an optional `b`, followed by any character, and then `t+` (one or more `t`s). The next character after the first `b` does not meet the pattern.
- Matches a string that starts with 0 or 1 `b` because `b?` insists that there should be no more than one `b`. The next should be any one character followed by `t`.


**`b?.t+$`**:
- This will **match** `bbbbbatttt` because it scans the string from left to right, allowing for zero or more `b`s, followed by one character, and ending with one or more `t`s at the end of the string.


**`^b?.t+$`**:
- This will **match** strings that start with zero or one `b`, followed by any character, and ending with one or more `t`s.
	`batttt`, `bbttttt`, `attttt`.


**`^0a*1+`**:
- This will match strings that start with a `0`, followed by zero or more `a`'s, and at least one `1`.
	`0a1`, `0aaaa111`, `101111`, `01`.
- There can be any character after `1`. `0a1a` `011100`


**`^0a*1+$`**:
- This variation **fixes** the ending part to ensure it ends with one or more `1`s, with no characters following the `1`. It will match:  `0a1`,  `0aaaa111`,  `10111`.

**`^$`**:    
- This matches the **empty string**. It asserts that there is nothing between the start and end of the string.


---

### Matching From a List of Options

When we want to match a **set of characters** without caring about their specific order to indicate "any of these", we can use **character classes**. 
These are defined with **square brackets** (`[]`), which specify that the next character in the string must match **any single character** from the list of options inside the brackets.

***Types of Lists:*** as given by the notation inside the bracket.

**Enumerated List**: `[abcd]` Matches **any one of** the characters `a`, `b`, `c`, or `d`, in any order. There should be no separators.

**Range**:  `[a-f]` Matches **any one of** the characters from `a` to `f`, inclusive. This is equivalent to writing `[a, b, c, d, e, f]`.

**Character Class**: A **character class** is a predefined group that matches a set of characters based on a certain property.
**`[:alpha:]`** matches **any alphabetic character** (equivalent to `[a-zA-Z]`).


- **`[abc][abc][abc]`** or **`[a-c][a-c][a-c]`**: This matches any **three consecutive characters** where each character is one of `a`, `b`, or `c`, in any combination. `abc`, `acb`, `bca`, `aaa`, `bbb`, `bcc`, `zyxaaa`, `@aaa@`, `aaaaa`, `1cba2`.
	`[abcxyz]` `[abcdABCD]` `[abc1234]`
    
- **Range Combinations**:
    - `[a-cx-z]` : Matches any character from the sets `a` to `c` **or** `x` to `z`.
    - `[a-d1-4]` : Matches any character from the sets `a` to `d` **or** `1` to `4`.
    - `[a-dA-D]` : Matches any character from the sets `a` to `d` **or** `A` to `D`.


* ***POSIX Character Classes***:
    - **`[[:alpha:]]`** which is equivalent to `[a-zA-Z]`.
    - **`[[:punct:]]`**. This matches any punctuation character such as `.`, `,`, `!`, etc. (there's no direct range for all punctuation marks).

___


***Combining `[]` with `* + ?`*** to control the number of times we expect the characters in the bracket to appear.
