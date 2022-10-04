# 112 - Path Sum

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/path-sum/
| Language | Python 3
| Runtime | 40 ms, faster than 97.79% of Python3 online submissions for Path Sum
| Memory Usage | 15.1 MB, less than 56.50% of Python3 online submissions for Path Sum
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
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root: return False
        if not root.left and not root.right and root.val == targetSum: return True
        return self.hasPathSum(root.left, targetSum-root.val) or self.hasPathSum(root.right, targetSum-root.val)
```
