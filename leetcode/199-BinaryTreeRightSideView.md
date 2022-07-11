# 199 - Binary Tree Right Side View

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/binary-tree-right-side-view/
| Language | Python 3
| Runtime | 42 ms, faster than 72.56% of Python3 online submissions for Binary Tree Right Side View
| Memory Usage | 13.8 MB, less than 97.84% of Python3 online submissions for Binary Tree Right Side View
| Datastructures | TreeNode
| Algorithms | DFS
| Complexity | Time: O(N) Memory: O(H) (N=number of nodes, H= height of tree)

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
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        result = []
        
        def dfs(root,depth):
            if root == None: return
            if depth == len(result): result.append(root.val)
            dfs(root.right, depth+1)
            dfs(root.left, depth+1)
        
        dfs(root,0)
        return result
```
