---
title: 3Sum
---

### Problem:
Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note: The solution set must not contain duplicate triplets.

```
For example, given array S = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```
***

### Analysis:
Sort the array and traverse the array from 0 ~ len(array) - 2. for each element i use i + 1 ~ len(array) - 2 do  2 sum. the new target is target - array[i]. repeat the process until find all solution. for each tuple i, j, k. if array[i]. Be careful the duplicates may cause duplicate solution.  Time complexity is O(n^2)

***

### Implementation:
```
def threeSum(self, nums):
    if len(nums) <3: 
        return []
    elif len(nums) == 3:
        if sum(nums) == 0:
            return [sorted(nums)]
    nums.sort()
    res = []
    for i in list(range(len(nums)-2)):
        if i > 0 and nums[i] == nums[i-1]: # avoid duplication
            continue
        j = i + 1
        k = len(nums) - 1
        while j < k:
            if j > i + 1 and nums[j] == nums[j-1]: # avoid duplication
                j += 1
                continue
            if k < len(nums) - 1 and nums[k] == nums[k+1]: # avoid duplication
                k -= 1
                continue
            if nums[i] + nums[j] + nums[k] == 0:
                res.append([nums[i],nums[j],nums[k]])
            if nums[i] + nums[j] + nums[k] < 0:
                j += 1
            else:
                k -= 1
    return res
```