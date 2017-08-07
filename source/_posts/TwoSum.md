---
title: Two Sum
---
### Problem:
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

### Example:

```
Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
***

### Analysis:
A hash table is built exactly for this purpose, it supports fast look up in near constant time. I say "near" because if a collision occurred, a look up could degenerate to O(n) time. But look up in hash table should be amortized O(1)time as long as the hash function was chosen carefully.

While we iterate and inserting elements into the table, we also look back to check if current element's complement already exists in the table. If it exists, we have found a solution and return immediately.

***

### HashMap:
Time Complexity
O(n) one pass We traverse the list containing n elements only once. Each look up in the table costs only O(1) time.
Space Complexity
O(n) The extra space required depends on the number of items stored in the hash table, which stores at most n elements.

***
### Implementation
```
def twoSum(self, nums, target):
        d={}
        for i,num in enumerate(nums):
            if target-num in d:
                return d[target-num]+1, i+1
            d[num]=i
```

***
### Follow up:
What if the element is between 0~9




