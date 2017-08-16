---
title: Remove Duplicates from Sorted Array
---

### Problem:
Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

For example,
Given input array nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the new length.

***

### Analysis:
Start from new index newTail=0, only put the number is larger than nums[newTail], then update newTail and nums[newTail]. repeat the process to find the result. The Time Complexity is O(n), Space Complexity is O(1).
***

### Implementation:
```
class Solution:
    # @param a list of integers
    # @return an integer
    def removeDuplicates(self, A):
        if not A:
            return 0

        newTail = 0

        for i in range(1, len(A)):
            if A[i] != A[newTail]:
                newTail += 1
                A[newTail] = A[i]

        return newTail + 1
```