---
title: Permutations 
---


### Problem:

Given a collection of distinct numbers, return all possible permutations.

For example,
```
[1,2,3] have the following permutations:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

***

### Analysis:
```
the basic idea is, to permute n numbers, we can add the nth number into the resulting two-demension result list from the n-1 numbers, in every possible position.

For example, if the input array is {1,2,3}. First, add 1 into the initial result list which is result.

Then, 2 can be added in front or after 1. So we have to copy the list in answer, it's just {1}, add 2 in position 0 of {1}, then copy the original {1} again, and add 2 in position 1. Now we have an answer of {{2,1},{1,2}}. There are 2 lists in the current result.

Then we have to add 3. first copy {2,1} and {1,2}, add 3 in position 0; then copy {2,1} and {1,2}, and add 3 into position 1, then do the same thing for position 3. Finally we have 2*3=6 lists in answer, which is what we want.

The Time Complexity is O(n!)
```
***

### Implementation:

```
def permute(self, nums):
    perms = [[]]
    for n in nums:
        new_perms = []
        for perm in perms:
            for i in xrange(len(perm)+1):
                new_perms.append(perm[:i] + [n] + perm[i:])   ###insert n
        perms = new_perms
    return perms
```

