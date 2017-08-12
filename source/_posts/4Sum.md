---
title: 4Sum
---

### Problem: 
Given an array S of n integers, are there elements a, b, c, and d in S such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.

Note: The solution set must not contain duplicate quadruplets.

```
For example, given array S = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```

***

### Ayalysis:
Similar to 3sum problem. This kind of questions can be solved by k Sum problem.

To avoid duplicate list items, I skip unnecessary indices at two locations:

one at the end of the outer loop (i-loop)
the other at the end of the inner loop (j-loop).
To avoid useless computations, the following is kind of critical:

the function return immediately when nums[i]*4 > target
the inner loop break immediately when nums[j]*4 < target.

Time Complexity is O(n^3)
***

### Implementation:

### Iterative:
```
class Solution:
# @return a list of lists of length 4, [[val1,val2,val3,val4]]
def fourSum(self, num, target):
    two_sum = collections.defaultdict(list)
    res = set()
    for (n1, i1), (n2, i2) in itertools.combinations(enumerate(num), 2):
        two_sum[i1+i2].append({n1, n2})
    for t in list(two_sum.keys()):
        if not two_sum[target-t]:
            continue
        for pair1 in two_sum[t]:
            for pair2 in two_sum[target-t]:
                if pair1.isdisjoint(pair2):
                    res.add(tuple(sorted(num[i] for i in pair1 | pair2)))
        del two_sum[t]
    return [list(r) for r in res]
```
### Recursive:
```
def fourSum(self, nums, target):
    nums.sort()
    results = []
    self.findNsum(nums, target, 4, [], results)
    return results

def findNsum(self, nums, target, N, result, results):
    if len(nums) < N or N < 2: return

    # solve 2-sum
    if N == 2:
        l,r = 0,len(nums)-1
        while l < r:
            if nums[l] + nums[r] == target:
                results.append(result + [nums[l], nums[r]])
                l += 1
                r -= 1
                while l < r and nums[l] == nums[l - 1]:
                    l += 1
                while r > l and nums[r] == nums[r + 1]:
                    r -= 1
            elif nums[l] + nums[r] < target:
                l += 1
            else:
                r -= 1
    else:
        for i in range(0, len(nums)-N+1):   # careful about range
            if target < nums[i]*N or target > nums[-1]*N:  # take advantages of sorted list
                break
            if i == 0 or i > 0 and nums[i-1] != nums[i]:  # recursively reduce N
                self.findNsum(nums[i+1:], target-nums[i], N-1, result+[nums[i]], results)
    return
```


### Revised:
```
def fourSum(self, nums, target):
    def findNsum(nums, target, N, result, results):
        if len(nums) < N or N < 2 or target < nums[0]*N or target > nums[-1]*N:  # early termination
            return
        if N == 2: # two pointers solve sorted 2-sum problem
            l,r = 0,len(nums)-1
            while l < r:
                s = nums[l] + nums[r]
                if s == target:
                    results.append(result + [nums[l], nums[r]])
                    l += 1
                    while l < r and nums[l] == nums[l-1]:
                        l += 1
                elif s < target:
                    l += 1
                else:
                    r -= 1
        else: # recursively reduce N
            for i in range(len(nums)-N+1):
                if i == 0 or (i > 0 and nums[i-1] != nums[i]):
                    findNsum(nums[i+1:], target-nums[i], N-1, result+[nums[i]], results)

    results = []
    findNsum(sorted(nums), target, 4, [], results)
    return results
```