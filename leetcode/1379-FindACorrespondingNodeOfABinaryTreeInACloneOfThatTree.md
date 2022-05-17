# 1379 - Find a Corresponding Node of a Binary Tree in a Clone of That Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/
| Language | Python 3
| Runtime | 926 ms, faster than 26.65% of Python3 online submissions for Find a Corresponding Node of a Binary Tree in a Clone of That Tree
| Memory Usage | 23.9 MB, less than 94.29% of Python3 online submissions for Find a Corresponding Node of a Binary Tree in a Clone of That Tree
| Datastructures | TreeNode (provided)
| Algorithms | DFS/recursion (can also use BFS w/ deque/queue/list)

### Procedure

1. Create resursive method for dfs
   1. If the provided node is null, return nothing
   2. If the node value matches the target value, return the node
   3. Search deeper (recurse left and right neighbors)
2. Return result of top-level (inital) dfs method call

### Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    def getTargetCopy(self, original: TreeNode, cloned: TreeNode, target: TreeNode) -> TreeNode:
        def dfs(node):
            if not node: return None
            if node.val == target.val: return node
            return dfs(node.left) or dfs(node.right)
        return dfs(cloned)
```
