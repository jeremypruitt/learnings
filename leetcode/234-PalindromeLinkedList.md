# 234 - Palindrome Linked List

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/palindrome-linked-list/
| Language | Python 3
| Runtime | 802 ms, faster than 94.42% of Python3 online submissions for Palindrome Linked List
| Memory Usage | 38.9 MB, less than 89.07% of Python3 online submissions for Palindrome Linked List
| Datastructures | ListNode
| Algorithms | Two-Pointers (fast/slow)
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
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        # ---------------------------------
        # Floyd's Cycle Detection Algorithm
        # ---------------------------------
        
        slow, fast, prev = head, head, None
        
        # Fast ptr moves through list at twice speed, so
        # when it hits the end the slow ptr is in the middle
        while fast and fast.next:
            slow, fast = slow.next, fast.next.next
        
        # Break  linked list in middle (prev.next = None)
        prev, slow, prev.next = slow, slow.next, None
        
        # Reverse the backj half with slow ptr
        while slow:
            slow.next, prev, slow = prev, slow, slow.next
        
        fast, slow = head, prev
        
        # Fast is now at beginning, and slow is at end,
        # and they both point (linked) towards the middle.
        # Now we just move inwards one step at a time and
        # compare each value. If they don't match then it
        # isn't a palindrome.ArithmeticError
        while slow:
            if fast.val != slow.val: return False
            fast, slow = fast.next, slow.next
        
        # If we make it this far it must be a palindrome
        return True
```
