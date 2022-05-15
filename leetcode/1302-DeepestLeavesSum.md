# 1302 - Deepest Leaves Sum

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/deepest-leaves-sum/
| Language | Python 3
| Runtime | 233 ms, faster than 79.40% of Python3 online submissions for Deepest Leaves Sum
| Memory Usage | 17.8 MB, less than 66.46% of Python3 online submissions for Deepest Leaves Sum

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def deepestLeavesSum(self, root: Optional[TreeNode]) -> int:
        next_level = [root]
        
        while next_level:
            this_level = next_level
            next_level = []
            
            for node in this_level:
                if node.left: next_level.append(node.left)
                if node.right: next_level.append(node.right)
        
        return sum([node.val for node in this_level])
```
