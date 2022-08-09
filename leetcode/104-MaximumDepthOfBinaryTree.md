# 104 - Maximum Depth of Binary Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/maximum-depth-of-binary-tree/
| Language | Python 3
| Runtime | 55 ms, faster than 71.41% of Python3 online submissions for Maximum Depth of Binary Tree
| Memory Usage | 16.6 MB, less than 23.50% of Python3 online submissions for Maximum Depth of Binary Tree
| Datastructures | TreeNode
| Algorithms | DFS
| Complexity | Time: O(N) Memory: O(logN)

### Procedure

1. ...

### Code

#### Option 1: Terse

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root: return 0
        return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1
```

#### Option 2: Verbose

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        depth = 1
        def dfs(node):
            nonlocal depth
            if not node: return 0
            if not node.left and not node.right: return 0
            depth += 1
            dfs(node.left)
            dfs(node.right)
        
        dfs(root)
        return depth
```
