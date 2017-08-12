---
title: 3Sum Closest
---

### Problem:
Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

```
    For example, given array S = {-1 2 1 -4}, and target = 1.

    The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

***

### Analysis:
Similar to 3 Sum problem, use 3 pointers to point current element, next element and the last element. If the sum is less than target, it means we have to add a larger element so next element move to the next. If the sum is greater, it means we have to add a smaller element so last element move to the second last element. Keep doing this until the end. Each time compare the difference between sum and target, if it is less than minimum difference so far, then replace result with it, otherwise keep iterating. Time Complexity is O(n^2)

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