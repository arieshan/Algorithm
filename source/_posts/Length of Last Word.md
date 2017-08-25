---
title: Length of Last Word
---

### Problem: 
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

For example, 
Given s = "Hello World",
return 5.

***

### Analysis:
Pretty easy one. Split the string and get last one's length. Time Complexity is O(n).

***

### Implementation:
```
def lengthOfLastWord(self, s):
    return len(s.rstrip(' ').split(' ')[-1])
```