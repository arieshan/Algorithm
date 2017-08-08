---
title: Longest Palindromic Substring
---
### Problem:
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

Example:

```
Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.
```


Example:

```
Input: "cbbd"

Output: "bb"
```
---
## Spread From Center:
start from the center of the string, spread to two ends. The process is same as the brute force. Check both odd and even cases and calculate the longest palindrome. Time Complexity O(n^2) space O(1)


```
def longestPalindrome(self, s):
    res = ""
    for i in xrange(len(s)):
        # odd case, like "aba"
        tmp = self.helper(s, i, i)
        if len(tmp) > len(res):
            res = tmp
        # even case, like "abba"
        tmp = self.helper(s, i, i+1)
        if len(tmp) > len(res):
            res = tmp
    return res
 
# get the longest palindrome, l, r are the middle indexes   
# from inner to outer
def helper(self, s, l, r):
    while l >= 0 and r < len(s) and s[l] == s[r]:
        l -= 1; r += 1
    return s[l+1:r]
```

---
## Dynamic Programming
if a long string is a palindrome, his specific substrings are also palindrome. For example, ABCCBA is a palindrome. BCCB is also a palindrome. So first we can calculate the strings whose length is 1. Then calculate the strings whose length is 2. When we calculate the strings whose length is 3 just use 1's string and 2's string. Repeat this process until find the longest one.Time Complexity is O(n^2), Space is O(n^2)


```
class Solution:
    # @return a string
    def longestPalindrome(self, s):
        if len(s)==0:
        	return 0
        maxLen=1
        start=0
        for i in xrange(len(s)):
        	if i-maxLen >=1 and s[i-maxLen-1:i+1] == s[i-maxLen-1:i+1][::-1]:
        		start=i-maxLen-1
        		maxLen+=2
        		continue

        	if i-maxLen >=0 and s[i-maxLen:i+1] == s[i-maxLen:i+1][::-1]:
        		start=i-maxLen
        		maxLen+=1
        return s[start:start+maxLen]
```

---
## Manacher Algorithm


Time Complexity is O(n) space is O(n)

---
## Follow Up
Q: if only can delete the character at the front of the string. find the lease number of the delete characters.
A: find the longest palindrome and calculate the difference. 


