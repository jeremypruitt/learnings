# 366 - Find Leaves of Binary Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-leaves-of-binary-tree/
| Language | Python 3
| Runtime | 26 ms, faster than 98.90% of Python3 online submissions for Find Leaves of Binary Tree
| Memory Usage | 13.8 MB, less than 98.46% of Python3 online submissions for Find Leaves of Binary Tree
| Datastructures | TreeNode
| Algorithms | DFS (postorder)
| Complexity | Time: O(NlogN) Memory: O(N)

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
    def findLeaves(self, root: Optional[TreeNode]) -> List[List[int]]:
        result = []
        
        def dfs(r):
            if r == None: return -1
            nonlocal result
            distance = max(dfs(r.left), dfs(r.right)) + 1
            if distance >= len(result):
                result.append([r.val])
            else:
                result[distance].append(r.val)
            return distance
            
        dfs(root)
        return result
```
