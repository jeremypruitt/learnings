# 1457 - Pseudo-Palindromic Paths in a Binary Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/pseudo-palindromic-paths-in-a-binary-tree/
| Language | Python 3
| Runtime | 1860 ms, faster than 15.58% of Python3 online submissions for Pseudo-Palindromic Paths in a Binary Tree
| Memory Usage | 85.1 MB, less than 71.65% of Python3 online submissions for Pseudo-Palindromic Paths in a Binary Tree
| Datastructures | TreeNode
| Algorithms | Backtracking
| Complexity | Time: O(N) Memory: O(K+H)

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
    def pseudoPalindromicPaths (self, root: Optional[TreeNode]) -> int:
        def dfs(node, cur):
            if not node: return 0
            result = 0
            
            if node.val in cur: cur.remove(node.val)
            else:               cur.add(node.val)
            
            if not node.left and not node.right:
                if len(cur) <= 1: result = 1
            else:
                result = result + dfs(node.left, cur) + dfs(node.right, cur)
            
            if node.val in cur: cur.remove(node.val)
            else:               cur.add(node.val)
            
            return result
        
        return dfs(root, set())
```
