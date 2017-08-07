---
title: Add Two Numbers
---
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Example
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```
***
### Analysis
Traverse both lists. One by one pick nodes of both lists and add the values. If sum is more than 10 then make carry as 1 and reduce sum. If one list has more elements than the other then consider remaining values of this list as 0. Following is the implementation of this approach. Time Complexity is O(m + n)
***
### Implementation
```
 def addTwoNumbers(self, l1, l2):
        carry = 0;
        res = n = ListNode(0);
        while l1 or l2 or carry:
            if l1:
                carry += l1.val
                l1 = l1.next;
            if l2:
                carry += l2.val;
                l2 = l2.next;
            carry, val = divmod(carry, 10)
            n.next = n = ListNode(val);
        return res.next;
```