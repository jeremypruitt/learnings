# 100 - Same Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/same-tree/
| Language | Python 3
| Runtime | 75 ms, faster than 5.27% of Python3 online submissions for Same Tree
| Memory Usage | 13.8 MB, less than 75.79% of Python3 online submissions for Same Tree
| Datastructures | TreeNode
| Algorithms | DFS
| Complexity | Time: O(N) Memory: O(H) (C=number of nodes in tree, H=height of tree)

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
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if not p or not q: return p == q
        if p.val != q.val: return False
        return self.isSameTree(p.left,q.left) and self.isSameTree(p.right,q.right)
```
