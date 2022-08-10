# 108 - Convert Sorted Array to Binary Search Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/
| Language | Python 3
| Runtime | 128 ms, faster than 52.36% of Python3 online submissions for Convert Sorted Array to Binary Search Tree
| Memory Usage | 15.6 MB, less than 83.29% of Python3 online submissions for Convert Sorted Array to Binary Search Tree
| Datastructures | TreeNode
| Algorithms | Binary Search / DFS
| Complexity | Time: O(N) Memory: O(logN)

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
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        def dfs(left,right):
            if left > right: return None
            mid = (left+right) // 2
            return TreeNode(nums[mid], dfs(left, mid - 1), dfs(mid+1, right))
        return dfs(0, len(nums)-1)
```
