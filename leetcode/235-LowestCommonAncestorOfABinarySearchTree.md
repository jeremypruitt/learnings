# 235 - Lowest Common Ancestor of a Binary Search Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/
| Language | Python 3
| Runtime | 122 ms, faster than 44.61% of Python3 online submissions for Lowest Common Ancestor of a Binary Search Tree
| Memory Usage | 18.9 MB, less than 22.45% of Python3 online submissions for Lowest Common Ancestor of a Binary Search Tree
| Datastructures | List[str]
| Algorithms | Iteration
| Complexity | Time: O(N) Memory: O(1)

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
        while root:
            if   p.val < root.val > q.val: root = root.left
            elif p.val > root.val < q.val: root = root.right
            else: return root
```
