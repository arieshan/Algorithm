---
title: Reverse Integer
---
### Problem

Reverse digits of an integer.

Example1: x = 123, return 321
Example2: x = -123, return -321

Note:
The input is assumed to be a 32-bit signed integer. Your function should return 0 when the reversed integer overflows.

***

### Analysis:
Get the sign, get the reversed absolute integer, and return their product if r didn't "overflow".

***

### Implementation
```
def reverse(self, x):
    s = cmp(x, 0)
    r = int(`s*x`[::-1])
    return s*r * (r < 2**31)
```