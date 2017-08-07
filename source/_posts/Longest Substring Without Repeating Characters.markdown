---
title: Longest Substring Without Repeating Characters
---
Given a string, find the length of the longest substring without repeating characters.

### Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

***

### Analysis
According to the definition of the longest unambiguous sub-string, we will encounter the characters in the current substring when traversing the string, and the new substring should start from the next bit of the repeat point. So in order to find the maximum length in a traversal, we need to record two things. The first is whether a letter appears in the current substring or not, and the second is what happens if it appears in the string. The easiest way to determine whether a character is present in the current substring is to see if it was the last occurrence of the first character of the current substring or the back of the first character, so we just record the character last position can meet both requirements at the same time. Hash table is the most natural idea. When traversing the string, we first find out the last occurrence of the character based on the hash table, and if it is greater than or equal to the substring, update the substring first. Because it is equivalent to a sub-string has ended, we have to update the maximum length. After the end of the character, put the new position into the hash table. Time complexity is O(n) and Space complexity is O(n)

### Tips
* 1 After finish the traverse, need to update the max length and consider the max length string at the end of the source string

* 2 The substring start index should be the duplicate element's index + 1

* 3 The input string might be null or empty

***

### Implementation
```
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        start = maxLength = 0
        usedChar = {}

        for i in range(len(s)):
            if s[i] in usedChar and start <= usedChar[s[i]]:
                start = usedChar[s[i]] + 1
            else:
                maxLength = max(maxLength, i - start + 1)

            usedChar[s[i]] = i

        return maxLength
```