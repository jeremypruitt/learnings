# 236 - Lowest Common Ancestor of a Binary Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/
| Language | Python 3
| Runtime | 120 ms, faster than 41.93% of Python3 online submissions for Lowest Common Ancestor of a Binary Tree
| Memory Usage | 26.3 MB, less than 33.29% of Python3 online submissions for Lowest Common Ancestor of a Binary Tree
| Datastructures | TreeNode
| Algorithms | DFS (postorder w/ recursion)
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def dfs(node):
            if node in (None, p, q): return node
            left, right = dfs(node.left), dfs(node.right)
            if left and right: return node
            else: return left or right
        
        return dfs(root)
```
