# 814 - Binary Tree Pruning

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/binary-tree-pruning/
| Language | Python 3
| Runtime | 43 ms, faster than 70.03% of Python3 online submissions for Binary Tree Pruning
| Memory Usage | 13.8 MB, less than 68.92% of Python3 online submissions for Binary Tree Pruning
| Datastructures | TreeNode
| Algorithms | DFS w/ Recursion
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
    def pruneTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        # Base case
        if not root: return None
        
        # Recursion
        root.left, root.right = self.pruneTree(root.left), self.pruneTree(root.right)
        
        # Target
        return root if root.val or root.left or root.right else None
```
