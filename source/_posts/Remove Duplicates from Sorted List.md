---
title: Remove Duplicates from Sorted List
---

### Problem: 
Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.

***

### Analysis:
Simple traverse the single list. Add the first non-duplicate node and skip all duplicate nodes. The Time Complexity is O(n)
***

### Implementation: 
```
def deleteDuplicates(self, head):
    cur = head
    while cur:
        while cur.next and cur.next.val == cur.val:
            cur.next = cur.next.next     # skip duplicated node
        cur = cur.next     # not duplicate of current node, move to next node
    return head
```