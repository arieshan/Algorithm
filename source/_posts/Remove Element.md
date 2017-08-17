---
title: Remove Element.md
---

### Problem:
Given an array and a value, remove all instances of that value in place and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

Example:
Given input array nums = [3,2,2,3], val = 3

Your function should return length = 2, with the first two elements of nums being 2.

***

### Analysis:
Starting from the left every time, we find a value that is the target value. So swap it out with an item starting from the right. We decrement end each time. As we know that the final item is the target value and only increment start when we know the value is ok. when start reaches end we know all items after that point are the target value so we can stop there. Time Complexity is O(n) and Space Complexity is O(1).

***

### Implementation:
```
  def removeElement(self, nums, val):
    start, end = 0, len(nums) - 1
    while start <= end:
        if nums[start] == val:
            nums[start], nums[end], end = nums[end], nums[start], end - 1
        else:
            start +=1
    return start
```