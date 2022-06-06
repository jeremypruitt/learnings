# 160 - Intersection of Two Linked Lists

### Details

| Key | Value |
| --- | ----- |
| Link |https://leetcode.com/problems/intersection-of-two-linked-lists/
| Language | Python 3
| Runtime | 271 ms, faster than 19.44% of Python3 online submissions for Intersection of Two Linked Lists
| Memory Usage | 29.5 MB, less than 93.74% of Python3 online submissions for Intersection of Two Linked Lists
| Datastructures | Linked List
| Algorithms | 2 pointers

### Procedure

1. TBD...

### Code

```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        p1, p2 = headA, headB
        while p1 is not p2:
            p1 = headB if p1 is None else p1.next
            p2 = headA if p2 is None else p2.next
        return p1
```
