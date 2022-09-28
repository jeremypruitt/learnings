# 19 - Remove Nth Node From End of List

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/remove-nth-node-from-end-of-list/submissions/
| Language | Python 3
| Runtime | 61 ms, faster than 39.26% of Python3 online submissions for Remove Nth Node From End of List
| Memory Usage | 13.8 MB, less than 70.33% of Python3 online submissions for Remove Nth Node From End of List
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
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        slow = fast = head
        
        # Advance fast pointer to nth position
        for _ in range(n): fast = fast.next
        
        # Edge case when head only has one node
        if not fast: return head.next
        
        # Fast and low are N apart, so we advance until fast reaches
        # end of the linked list.
        while fast.next: slow, fast = slow.next, fast.next
        
        # The nth node is now the next node, so remove/overwrite it.
        slow.next = slow.next.next
        
        return head
```
