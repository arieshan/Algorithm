---
title: Remove Duplicates from Sorted Array II
---

### Problem:
Follow up for "Remove Duplicates":
What if duplicates are allowed at most twice?

For example,
Given sorted array nums = [1,1,1,2,2,3],

Your function should return length = 5, with the first five elements of nums being 1, 1, 2, 2 and 3. It doesn't matter what you leave beyond the new length.

***

### Analysis:
go through the numbers and include those in the result that haven't been included twice already.

Time Complexity is O(n)

***

### Implementation:
```
def removeDuplicates(self, nums):
    i = 0
    for n in nums:
        if i < 2 or n > nums[i-2]:
            nums[i] = n
            i += 1
    return i
```
 