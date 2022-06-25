# 876 - Middle of the Linked List

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/middle-of-the-linked-list/
| Language | Python 3
| Runtime | 36 ms, faster than 79.89% of Python3 online submissions for Middle of the Linked List
| Memory Usage | 13.9 MB, less than 10.64% of Python3 online submissions for Middle of the Linked List
| Datastructures | Linked List
| Algorithms | Two Pointer (fast/slow)
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. While slow moves one step forward, fast moves two steps forward.
2. When fast reaches the end, slow is in the middle of linked list.

### Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        slow = fast = head
        
        while fast and fast.next:
            slow, fast = slow.next, fast.next.next
        
        return slow
```
