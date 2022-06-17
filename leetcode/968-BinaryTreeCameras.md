# 968 - Binary Tree Cameras

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/binary-tree-cameras/
| Language | Python 3
| Runtime | 39 ms, faster than 98.12% of Python3 online submissions for Binary Tree Cameras
| Memory Usage | 14.2 MB, less than 56.67% of Python3 online submissions for Binary Tree Cameras
| Datastructures | TreeNode
| Algorithms | DP (bottom-up)
| Complexity | Time: O(n) Memory: O(h) (h = height of tree)

### Procedure

1. ...

### Code

#### Option 1: Greedy DP (bottom-up, faster)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def minCameraCover(self, root: Optional[TreeNode]) -> int:
        def dfs(node):
            if not node: return 1
            left  = dfs(node.left)
            right = dfs(node.right)
            
            if left == 0 or right == 0:
                self.sum += 1
                return 2
            elif left == 2 or right == 2:
                return 1
            else:
                return 0
        
        self.sum = 0
        if dfs(root) == 0: self.sum += 1
        
        return self.sum
```

#### Option 2: DP (slower)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def minCameraCover(self, root: Optional[TreeNode]) -> int:
        @cache
        def dp(node, forced = None):
            # Here, forced == None means that the parent either doesn't
            # exist or needs not be considered at all i.e. treat current
            # node as an independent tree (parent has no camera but is
            # taken care of by its parent or its other child).
            #
            # forced == False means that the parent node has a camera so
            #           the current node IS NOT FORCED to have a camera.
            #
            # forced == True means that the current node IS FORCED TO
            #           have a camera and there is no other alternative.
            
            if not node:
                return 0
            
            temp = 1 + dp(node.left, False) + dp(node.right, False)
            
            if forced is None:
                if node.left:
                    temp = min(temp, dp(node.left, True) + dp(node.right, None))
                if node.right:
                    temp = min(temp, dp(node.left, None) + dp(node.right, True))
                return temp
            
            if forced is False:
                return min(temp, dp(node.left, None) + dp(node.right, None))
            
            return temp
        
        return dp(root)
```
