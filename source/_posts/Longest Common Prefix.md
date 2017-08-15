---
title: Longest Common Prefix
---

### Problem:
Write a function to find the longest common prefix string amongst an array of strings.

***

### Analysis:
use two loops check from the start of both string, find the mismatch position and return. The shorter one's length is the end of the loop. Need to consider no prefix and whole match these two conditions.

***

### Implementation:

```
 def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        if not strs:
            return ""
        shortest = min(strs,key=len)
        for i, ch in enumerate(shortest):
            for other in strs:
                if other[i] != ch:
                    return shortest[:i]
        return shortest 
```