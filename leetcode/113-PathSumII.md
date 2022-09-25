# 113 - Path Sum II

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/path-sum-ii/submissions/
| Language | Python 3
| Runtime | 51 ms, faster than 87.32% of Python3 online submissions for Path Sum II
| Memory Usage | 15.6 MB, less than 72.84% of Python3 online submissions for Path Sum II
| Datastructures | TreeNode
| Algorithms | DFS
| Complexity | Time: O(N^2) Memory: O(N)

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
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
        
        def dfs(node: TreeNode, targetSum: int):
            if not node: return []
            if not node.left and not node.right and targetSum == node.val:
                return [[node.val]]
            
            left  = dfs(node.left,  targetSum - node.val)
            right = dfs(node.right, targetSum - node.val)
            
            return [cand + [node.val] for cand in left + right]
            
        return [result[::-1] for result in dfs(root, targetSum)]
```
