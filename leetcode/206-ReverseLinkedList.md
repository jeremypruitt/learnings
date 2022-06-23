# 206 - Reverse Linked List

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/reverse-linked-list/
| Language | Python 3
| Runtime | 54 ms, faster than 48.90% of Python3 online submissions for Reverse Linked List
| Memory Usage | 15.4 MB, less than 55.56% of Python3 online submissions for Reverse Linked List
| Datastructures | ListNode (linked list)
| Algorithms | Iterative
| Complexity | Time: O(n) Space: O(1)

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
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        last = None
        while head:
            last, head.next, head = head, last, head.next
        
        return last
```
