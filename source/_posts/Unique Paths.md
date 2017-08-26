---
title: Unique Paths
---

### Problem:
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

Above is a 3 x 7 grid. How many possible unique paths are there?

Note: m and n will be at most 100.

source link: https://leetcode.com/problems/unique-paths/description/

***

### Analysis:
Since the robot can only move right and down, when it arrives at a point, there are only two possibilities:

It arrives at that point from above (moving down to that point);
It arrives at that point from left (moving right to that point).
Thus, we have the following state equations: suppose the number of paths to arrive at a point (i, j) is denoted as P[i][j], it is easily concluded that P[i][j] = P[i - 1][j] + P[i][j - 1].

The boundary conditions of the above equation occur at the leftmost column (P[i][j - 1] does not exist) and the uppermost row (P[i - 1][j] does not exist). These conditions can be handled by initialization (pre-processing) --- initialize P[0][j] = 1, P[i][0] = 1 for all valid i, j. Note the initial value is 1 instead of 0!
Time Complexity is O(m * n), Space Complexity is O(m * n)

***

### Implementation: 

```
class Solution:
    # @return an integer
    def uniquePaths(self, m, n):
        aux = [[1 for x in range(n)] for x in range(m)]
        for i in range(1, m):
            for j in range(1, n):
                aux[i][j] = aux[i][j-1]+aux[i-1][j]
        return aux[-1][-1]
```

***

### Optimization:
The sliding array is a good way to save space. The space complexity is O(min(m, n))

```
class Solution:
    # @return an integer
    def c(self, m, n):
        mp = {}
        for i in range(m):
            for j in range(n):
                if(i == 0 or j == 0):
                    mp[(i, j)] = 1
                else:
                    mp[(i, j)] = mp[(i - 1, j)] + mp[(i, j - 1)]
        return mp[(m - 1, n - 1)]

    def uniquePaths(self, m, n):
        return self.c(m, n)
```