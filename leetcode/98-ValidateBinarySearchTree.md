# 98 - Validate Binary Search Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/validate-binary-search-tree/
| Language | Python 3
| Runtime | 103 ms, faster than 5.65% of Python3 online submissions for Validate Binary Search Tree
| Memory Usage | 16.4 MB, less than 78.23% of Python3 online submissions for Validate Binary Search Tree
| Datastructures | TreeNode
| Algorithms | Recursion
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
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        return self.validateBST(root, float("-inf"), float("inf"))
    
    def validateBST(self, node, left, right):
        # Empty tree is valid BST
        if not node: return True
        
        # Node value must be between left/right
        if not left < node.val < right: return False
        
        # Ensure left and right are valid
        return (
            self.validateBST(node.left, left, node.val) and
            self.validateBST(node.right, node.val, right)
        )
```
