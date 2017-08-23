---
title: Permutations II
---

### Problem:

Given a collection of numbers that might contain duplicates, return all possible unique permutations.

For example,
```
[1,1,2] have the following unique permutations:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```

***

### Analysis:
Similar to Permutations. Just need handle duplicate cases. To handle duplication, just avoid inserting a number before any of its duplicates. Time Complexity is O(n).

***

### Implementation:

```
def permuteUnique(self, nums):
    ans = [[]]
    for n in nums:
        new_ans = []
        for l in ans:
            for i in xrange(len(l)+1):
                new_ans.append(l[:i]+[n]+l[i:])
                if i<len(l) and l[i]==n: break              #handles duplication
        ans = new_ans
    return ans
```

Or

```
def permuteUnique(self, nums):
    ans = [[]]
    for n in nums:
        ans = [l[:i]+[n]+l[i:]
               for l in ans
               for i in xrange((l+[n]).index(n)+1)]
    return ans
```