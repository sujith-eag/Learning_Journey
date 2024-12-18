#22aug24

# 1071 GCD of strings 
### Question
```c
For two strings `s` and `t`, we say "`t` divides `s`" 
if and only if `s = t + t + t + ... + t + t`
(i.e., `t` is concatenated with itself one or more times).

Given two strings `str1` and `str2`, return the largest string `x` such that `x` divides both `str1` and `str2`.

**Example 1:**
**Input:** str1 = "ABCABC", str2 = "ABC"
**Output:** "ABC"

**Example 2:**
**Input:** str1 = "ABABAB", str2 = "ABAB"
**Output:** "AB"

**Example 3:**
**Input:** str1 = "LEET", str2 = "CODE"
**Output:** ""
```

### Tip
```c
Given two strings, check if they are made from same 'seed' or not
   
   > method 1 
	 > find gcd of 2 lengths
	 > take a gcd-length-section of any string
	 > see if that 'seed' can be used to make both the strings using a function
	 > if yes, "seed" is answer
	 > if no, there is no seed

   > method 2
	 > check if string1+string2 == string2+string1, if it is made of same seed, it will be symetric and similar, if it is not same, no seed
	 >  if same, find gcd of length, cut a gcd section, it is the 'seed'

> Assign values at a time while deciding max min in gcd, took some time to see assignment one after the other messes up the second value
```
### Solutions (2 versions)
```python
def GCDstri(s1, s2):
    def gcd(x, y):
        (x, y) = ( max(x, y), min(x, y))   # needs simultaneous assignment idiot
        if x % y == 0:    # base: return if divides without remainder    
            return y         
        else:
            while y>0:       # when y becomes 0 it will be false
                x, y = y, x%y
            return x        # return what divided y
            
    def constructor(s, factor):
        return s == factor * (len(s)//len(factor))   
        # len of factor is GCD
        # to build the same length as stri and see if it matches    

    x = len(s1)
    y = len(s2)
  
    gcd_no = gcd(x,y)
    factor = str1[0:gcd_no]  # string which has gcd no of elements

    # if both were made by same string
    if constructor(s1, factor) and constructor(s2, factor):
        print(factor)
    else:
        print("")

str1 = "TAUXXTAUXXTAUXXTAUXXTAUXXTAUXXTAUXXTAUXXTAUXX"
str2 = "TAUXXTAUXXTAUXXTAUXXTAUXX"
GCDstri(str1,str2)
# TAUXX
```

```python
def gcdOfStrings(str1: str, str2: str) -> str:
        
        if str1 + str2 != str2 + str1:   # How cool is this!!!
            return ""   # not symetric means no seed

        x = len(str1)
        y = len(str2)

        def find_gcd(x,y):
            (x,y) = (max(x,y),min(x,y))
            if x%y == 0:
                return y
            else:
                while y>0:
                    x, y = y, x%y
                    
                return x
                
        gcd = find_gcd(x,y)
        part = str1[0:gcd]
        return part

str1 = "TAUXXTAUXXTAUXXTAUXXTAUXXTAUXXTAUXXTAUXXTAUXX"
str2 = "TAUXXTAUXXTAUXXTAUXXTAUXX"
print(gcdOfStrings(str1,str2))

# TAUXX
```