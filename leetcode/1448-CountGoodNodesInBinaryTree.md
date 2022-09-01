# 1448 - Count Good Nodes in Binary Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/count-good-nodes-in-binary-tree/
| Language | Python 3
| Runtime | 286 ms, faster than 84.96% of Python3 online submissions for Count Good Nodes in Binary Tree
| Memory Usage | 32.6 MB, less than 16.88% of Python3 online submissions for Count Good Nodes in Binary Tree
| Datastructures | List[str]
| Algorithms | DFS w/ Recursion (also example with iteration + stack)
| Complexity | Time: O(N) Memory: O(H) (N=number of nodes, H=height of tree)

### Procedure

1. ...

### Code

#### Option 1: Recursion

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def goodNodes(self, root: TreeNode) -> int:
        def dfs(node: TreeNode, current_max: int):
            if node is None: return 0
            valid_node = node.val >= current_max
            current_max = max(node.val, current_max)
            left, right = dfs(node.left, current_max), dfs(node.right, current_max)
            return valid_node + left + right
        
        return dfs(root, root.val)
```

#### Option 2: Recursion w/o New Function

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def goodNodes(self, root: TreeNode, current_max = -math.inf) -> int:
        if root == None: return 0
        left = self.goodNodes(root.left, max(current_max, root.val))
        right = self.goodNodes(root.right, max(current_max, root.val))
        return (current_max <= root.val) + left + right
```

#### Option 3: Iteration w/ Stack

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def goodNodes(self, root: TreeNode) -> int:
        count, stack = 0, [(root, root.val)]
        while stack:
            current_node, current_max_val = stack.pop()
            count += current_node.val >= current_max_val
            for child in current_node.left, current_node.right:
                if child: stack.append((child, max(current_node.val, current_max_val)))
        return count
```
