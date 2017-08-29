---
title: Decode Ways
---

### Problem:
A message containing letters from A-Z is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```

Given an encoded message containing digits, determine the total number of ways to decode it.

For example,
Given encoded message "12", it could be decoded as "AB" (1 2) or "L" (12).

The number of ways decoding "12" is 2.

*** 

### Analysis:
used a dp array of size n + 1 to save subproblem solutions. dp[0] means an empty string will have one way to decode, dp[1] means the way to decode a string of size 1. I then check one digit and two digit combination and save the results along the way. In the end, dp[n] will be the end result. The Time Complexity is O(n), Space Complexity is O(n)

***


### Implementation:
```
def numDecodings(self, s):
    if not s:
        return 0

    dp = [0 for x in range(len(s) + 1)]
    dp[0] = 1
    dp[1] = 1 if 0 < int(s[0]) <= 9 else 0

    for i in range(2, len(s) + 1):
        if 0 < int(s[i-1:i]) <= 9:
            dp[i] += dp[i - 1]
        if s[i-2:i][0] != '0' and int(s[i-2:i]) <= 26:
            dp[i] += dp[i - 2]
    return dp[len(s)]
```

***

### O(1) Space Solution

```
def numDecodings(self, s):
    v, w, p = 0, int(s>''), ''
    for d in s:
        v, w, p = w, (d>'0')*w + (9<int(p+d)<27)*v, d
    return w
```

w tells the number of ways

v tells the previous number of ways

d is the current digit

p is the previous digit

reference: https://discuss.leetcode.com/topic/19042/1-liner-o-1-space/2
