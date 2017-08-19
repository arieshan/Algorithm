---
title: First Missing Positive
---

### Problem:
Given an unsorted integer array, find the first missing positive integer.

For example,
Given [1,2,0] return 3,
and [3,4,-1,1] return 2.

Your algorithm should run in O(n) time and uses constant space.

***

### Analysis:
Put each number in its right place.

For example:

When we find 5, then swap it with A[4].

At last, the first place where its number is not right, return the place + 1.

Time Complexity is O(n) and Space complexity is O(1)
***

### Implementation:
```
def firstMissingPositive(self, nums):
    for i in xrange(len(nums)):
        while 0 <= nums[i]-1 < len(nums) and nums[nums[i]-1] != nums[i]:
            tmp = nums[i]-1
            nums[i], nums[tmp] = nums[tmp], nums[i]
    for i in xrange(len(nums)):
        if nums[i] != i+1:
            return i+1
    return len(nums)+1
```