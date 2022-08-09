# 94 - Binary Tree Inorder Traversal

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/binary-tree-inorder-traversal/
| Language | Python 3
| Runtime | 36 ms, faster than 83.33% of Python3 online submissions for Binary Tree Inorder Traversal
| Memory Usage | 13.8 MB, less than 59.95% of Python3 online submissions for Binary Tree Inorder Traversal
| Datastructures | TreeNode
| Algorithms | DFS (inorder w/ recursion)
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
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        result = []
        def inorder(node):
            if not node: return None
            inorder(node.left)
            result.append(node.val)
            inorder(node.right)
        
        inorder(root)
        return result
```
