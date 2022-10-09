# 653 - Two Sum IV - Input is a BST

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/two-sum-iv-input-is-a-bst/submissions/
| Language | Python 3
| Runtime | 109 ms, faster than 80.11% of Python3 online submissions for Two Sum IV - Input is a BST
| Memory Usage | 16.3 MB, less than 82.46% of Python3 online submissions for Two Sum IV - Input is a BST
| Datastructures | TreeNode, Set
| Algorithms | BFS
| Complexity | Time: O(N) Memory: O(N) (C=number of characters in all words in array)

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
    def findTarget(self, root: Optional[TreeNode], k: int) -> bool:
        if not root: return False
        
        nodes, memo = [root], set()
        
        for node in nodes:
            if k - node.val in memo: return True
        
            memo.add(node.val)
            
            if node.left:  nodes.append(node.left)
            if node.right: nodes.append(node.right)
        
        return False
```
