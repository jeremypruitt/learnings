# 21 - Merge Two Sorted Lists

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/merge-two-sorted-lists/
| Language | Python 3
| Runtime | 91 ms, faster than 5.08% of Python3 online submissions for Merge Two Sorted Lists
| Memory Usage | 13.9 MB, less than 78.51% of Python3 online submissions for Merge Two Sorted Lists
| Datastructures | ListNode
| Algorithms | Iterative merge, no dummy
| Complexity | Time: O(n), Space: O(1)

### Procedure

1. Advance seek via its next attribute until seek.next overtakes target.val or reaches the end of the list.
2. Change the next attribute of seek to equal target, to stitch them together in sorted order.
3. Set seek to the previous value of target and set target to the previous value of seek.next.

### Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        if not list1 and not list2: return list1
        if not list1 or not list2:  return list1 if not list2 else list2
        
        seek, target = (list1, list2) if list1.val < list2.val else (list2, list1)
        head = seek
        
        while seek and target:
            while seek.next and seek.next.val < target.val:
                seek = seek.next

            seek.next, target = target, seek.next
            seek = seek.next
        
        return head
```
