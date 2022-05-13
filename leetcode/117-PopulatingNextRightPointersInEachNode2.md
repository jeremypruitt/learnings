# 117 - Populating Next Right Pointers in Each Node II

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/
| Language | Python 3
| Runtime | 59 ms, faster than 63.82% of Python3 online submissions for Populating Next Right Pointers in Each Node II.
| Memory Usage | 15.3 MB, less than 92.97% of Python3 online submissions for Populating Next Right Pointers in Each Node II.

```bash
"""
# Definition for a Node.
class Node:
    def __init__(self, val: int = 0, left: 'Node' = None, right: 'Node' = None, next: 'Node' = None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next
"""
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        queue = [root]
        
        while queue:
            previous = None
            
            queue_length = len(queue)
            for index in range(queue_length):
                current = queue[index]
                
                if previous: previous.next = current
                if current and current.left: queue.append(current.left)
                if current and current.right: queue.append(current.right)

                previous = current
            
            queue = queue[queue_length:]
        return root
```
