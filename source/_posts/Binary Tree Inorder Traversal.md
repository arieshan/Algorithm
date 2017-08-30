---
title: Binary Tree Inorder Traversal
---

### Problem:
Given a binary tree, return the inorder traversal of its nodes' values.

For example:
Given binary tree [1,null,2,3],
```
   1
    \
     2
    /
   3
```
return [1,3,2].

Note: Recursive solution is trivial, could you do it iteratively?

***

### Analysis:
Use a stack to store the parent node until find the left-most leaf node. then pop one node from the stack visit its right child and repeat the same process. until all nodes are visited. Time Complexity is O(n) Space Complexity is O(h) where h is the height of the tree.

***

### Implementation:
```
def inorderTraversal(self, root):
    res, stack = [], []
    while True:
        while root:
            stack.append(root)
            root = root.left
        if not stack:
            return res
        node = stack.pop()
        res.append(node.val)
        root = node.right
```