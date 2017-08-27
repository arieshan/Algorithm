---
title: Set Matrix Zeroes
---

### Problem:
Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in place.

Follow up:
Did you use extra space?
A straight forward solution using O(mn) space is probably a bad idea.
A simple improvement uses O(m + n) space, but still not the best solution.
Could you devise a constant space solution?

***

### Analysis:
store states of each row in the first of that row, and store states of each column in the first of that column. Because the state of row0 and the state of column0 would occupy the same cell, I let it be the state of row0, and use another variable "col0" for column0. In the first phase, use matrix elements to set states in a top-down way. In the second phase, use states to set matrix elements in a bottom-up way. Time Complexity is O(m * n), Space Complexity is O(1)

***

### Implementation:
```
class Solution(object):
def setZeroes(self, matrix):
    """
    :type matrix: List[List[int]]
    :rtype: void Do not return anything, modify matrix in-place instead.
    """
    height = len(matrix)
    if(height ==0): return
    width = len(matrix[0])
    for i in range(height):
        for j in range(width):
            if matrix[i][j] == 0:
                for tmp in range(height):
                    if matrix[tmp][j] != 0:
                        matrix[tmp][j] = 'a'
                for tmp in range(width):
                    if matrix[i][tmp] != 0: 
                        matrix[i][tmp] = 'a'

    for i in range(height):
        for j in range(width):
            if matrix[i][j] == 'a':
                matrix[i][j] = 0
```