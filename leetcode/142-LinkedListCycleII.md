# 142 - Linked List Cycle II

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/linked-list-cycle-ii/submissions/
| Language | Python 3
| Runtime | 48 ms, faster than 96.90% of Python3 online submissions for Linked List Cycle II
| Memory Usage | 17.3 MB, less than 94.26% of Python3 online submissions for Linked List Cycle II
| Datastructures | Linked List w/ Cycle
| Algorithms | Two Pointer
| Complexity | Time: O(N) Memory: O(1)

### Procedure

> "Imagine it this way, fast pointer moves faster than slow pointer by 1
> that is, from slow pointer point of view it is not moving and the fast
> pointer is moving at speed = 1 node per step. So, at some point, if
> there is a loop, fast pointer meets the slow pointer.
> 
> Now lets consider fast pointer to be moving at 3 nodes per step and
> slow pointer at 1 node per step. This is same as slow pointer no
> moving and fast pointer moving at 2 nodes per step. Now in this case
> we can not guarantee that fast pointer would meet the slow pointer
> because fast pointer might skip over the slow pointer since it is
> moving at 2 nodes per step."
>
>   -- *atomsareweird*

### Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next: return None
        if head.next is head: return head
        
        slow = fast = head
        
        while fast and fast.next:
            slow, fast = slow.next, fast.next.next
            if slow is fast: break
        else:
            return None
        
        slow = head
        while slow is not fast:
            slow, fast = slow.next, fast.next
        
        return slow
```
