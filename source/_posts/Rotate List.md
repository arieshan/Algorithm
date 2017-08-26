---
title: Rotate List
---

### Problem:
Given a list, rotate the list to the right by k places, where k is non-negative.

For example:
Given 1->2->3->4->5->NULL and k = 2,
return 4->5->1->2->3->NULL.

***

### Analysis:
Since n may be a large number compared to the length of list. So we need to know the length of linked list.After that, move the list after the (l-n%l )th node to the front to finish the rotation.

Ex: {1,2,3} k=2 Move the list after the 1st node to the front

Ex: {1,2,3} k=5, In this case Move the list after (3-5%3=1)st node to the front.

So the code has three parts.

Get the length

Move to the (l-n%l)th node

3)Do the rotation

Time Complexity is O(n)

***

### Implementation:
```
class Solution(object):
def rotateRight(self, head, k):
    """
    :type head: ListNode
    :type k: int
    :rtype: ListNode
    """
    if not head:
        return None
    
    if head.next == None:
        return head
        
    pointer = head
    length = 1
    
    while pointer.next:
        pointer = pointer.next
        length += 1
    
    rotateTimes = k%length
    
    if k == 0 or rotateTimes == 0:
        return head
    
    fastPointer = head
    slowPointer = head
    
    for a in range (rotateTimes):
        fastPointer = fastPointer.next
    
    
    while fastPointer.next:
        slowPointer = slowPointer.next
        fastPointer = fastPointer.next
    
    temp = slowPointer.next
    
    slowPointer.next = None
    fastPointer.next = head
    head = temp
    
    return head
```