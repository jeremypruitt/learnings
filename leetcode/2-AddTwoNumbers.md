# 2 - Add Two Numbers

Link: https://leetcode.com/problems/add-two-numbers/
Language: Python 3
Runtime: 84 ms, faster than 59.53% of Python3 online submissions for Add Two Numbers.
Memory Usage: 13.9 MB, less than 87.34% of Python3 online submissions for Add Two Numbers.

```bash
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        current = dummy
        carry = 0
        
        while l1 or l2 or carry:
            v1 = l1.val if l1 else 0
            v2 = l2.val if l2 else 0
            
            carry, value = divmod(v1 + v2 + carry, 10)
            # OR
            #value = l1 + l2 + carry
            #carry = value // 10
            #value = value % 10
            
            current.next = ListNode(value)
            current = current.next
            
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
        
        return dummy.next
```
