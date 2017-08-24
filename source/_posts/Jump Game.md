---
title: Jump Game
---

### Problem:
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

For example:
A = [2,3,1,1,4], return true.

A = [3,2,1,0,4], return false.

***

### Analysis:
If consider from the front, it can't be a greedy solution
however, if you think from the back, it IS greedy, why?

when at index i, you can jump to index i + nums[i]
so backwardly, the first goal is jumping to the index, target == len(nums) - 1
If find a index i, s.t. i + nums[i] >= len(nums) - 1, which means that as long as we can somehow greedily find a index j, s.t. j + nums[j] >= i, then we can sure we can jump from j to i.
So simply change target to i, and continuously doing backward!!
And in the end, since we are in the index 0 at the begining, and we keep updating our goal to i,
which means that if we (somehow) can jump to 0, which we already did, then we must be able to jump to len(nums) - 1!!

Time Complexity is O(n)

***

### Implementation:

```
class Solution(object):
    def canJump(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        target = len(nums) - 1
        for i in range(len(nums) - 2, -1, -1):
            if i + nums[i] >= target:
                target = i
        return target == 0
```