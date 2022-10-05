# 623 - Add One Row to Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/add-one-row-to-tree/
| Language | Python 3
| Runtime | 85 ms, faster than 60.61% of Python3 online submissions for Add One Row to Tree
| Memory Usage | 17.5 MB, less than 37.27% of Python3 online submissions for Add One Row to Tree
| Datastructures | TreeNode
| Algorithms | DFS
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
    def addOneRow(self, root: Optional[TreeNode], val: int, depth: int) -> Optional[TreeNode]:
        if not root or depth <= 0: return None
        
        if depth == 1: return TreeNode(val, root, None)
        if depth == 2:
            root.left  = TreeNode(val, root.left, None)
            root.right = TreeNode(val, None, root.right)
        else:
            root.left  == self.addOneRow(root.left,  val, depth - 1)
            root.right == self.addOneRow(root.right, val, depth - 1)
        
        return root
```
