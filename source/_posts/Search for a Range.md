---
title: Search for a Range
---

### Problem: 
Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

For example,
Given [5, 7, 7, 8, 8, 10] and target value 8,
return [3, 4].

***

### Analysis:
The helper function is a simple binary search, telling me the first index where I could insert a number n into nums to keep it sorted. Thus, if nums contains target, I can find the first occurrence with search(target). I do that, and if target isn't actually there, then I return [-1, -1]. Otherwise, I ask search(target+1), which tells me the first index where I could insert target+1, which of course is one index behind the last index containing target, so just let left to do is subtract 1. The Time Complexity is O(logn)

Here is a really good idea from StefanPochmann. Using Divide and Conquer: https://discuss.leetcode.com/topic/16486/9-11-lines-o-log-n 

### Implementation:
```
def searchRange(self, nums, target):
    def search(n):
        lo, hi = 0, len(nums)
        while lo < hi:
            mid = (lo + hi) / 2
            if nums[mid] >= n:
                hi = mid
            else:
                lo = mid + 1
        return lo
    lo = search(target)
    return [lo, search(target+1)-1] if target in nums[lo:lo+1] else [-1, -1]
```
