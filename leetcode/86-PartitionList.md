# 86 - Partition List

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/partition-list/
| Language | Python 3
| Runtime | 66 ms, faster than 23.14% of Python3 online submissions for Partition List
| Memory Usage | 14 MB, less than 31.57% of Python3 online submissions for Partition List
| Datastructures | ListNode
| Algorithms | Two-Pointers
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def partition(self, head: Optional[ListNode], x: int) -> Optional[ListNode]:
        small, large = ListNode(-1), ListNode(-1)
        small_head, large_head = small, large
        
        while head:
            if head.val < x:
                small.next = head
                head = head.next
                small = small.next
                small.next = None
            else:
                large.next = head
                head = head.next
                large = large.next
                large.next = None
        
        small.next = large_head.next
        
        return small_head.next
```
