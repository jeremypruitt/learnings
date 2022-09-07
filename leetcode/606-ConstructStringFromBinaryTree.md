# 606 - Construct String from Binary Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/construct-string-from-binary-tree/
| Language | Python 3
| Runtime | 65 ms, faster than 77.11% of Python3 online submissions for Construct String from Binary Tree
| Memory Usage | 16.4 MB, less than 72.23% of Python3 online submissions for Construct String from Binary Tree
| Datastructures | TreeNode
| Algorithms | DFS w/ Recursion
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

#### Option 1: Faster

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def tree2str(self, root: Optional[TreeNode]) -> str:
        if not root: return ""
        
        result = str(root.val)
        if root.left:
            result += f'({self.tree2str(root.left)})'
            if root.right:
                result += f'({self.tree2str(root.right)})'
        elif root.right:
            result += f'()({self.tree2str(root.right)})'
        
        return result
```

#### Option 2: Terse

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def tree2str(self, root: Optional[TreeNode]) -> str:
        if root is None: return ''
        if root.left  == None and root.right == None: return str(root.val)        
        if root.right == None: return f'{str(root.val)}({self.tree2str(root.left)})'
        return f'{str(root.val)}({self.tree2str(root.left)})({self.tree2str(root.right)})'
```
