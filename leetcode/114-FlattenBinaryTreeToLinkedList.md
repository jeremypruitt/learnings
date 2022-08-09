# 114 - Flatten Binary Tree to Linked List

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/flatten-binary-tree-to-linked-list/
| Language | Python 3
| Runtime | 57 ms, faster than 57.57% of Python3 online submissions for Flatten Binary Tree to Linked List
| Memory Usage | 15.3 MB, less than 11.27% of Python3 online submissions for Flatten Binary Tree to Linked List
| Datastructures | Stack, TreeNode
| Algorithms | Iterate + Stack
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def flatten(self, root: Optional[TreeNode]) -> None:
        """
        Do not return anything, modify root in-place instead.
        """
        if not root: return
        stack, dummy = [root], ListNode(0)
        
        while stack:
            node = stack.pop()
            if node.right: stack.append(node.right)
            if node.left:  stack.append(node.left)
            
            dummy.left, dummy.right = None, node
            dummy = dummy.right
```
