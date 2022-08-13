# 314 - Binary Tree Vertical Order Traversal

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/binary-tree-vertical-order-traversal/
| Language | Python 3
| Runtime | 53 ms, faster than 51.99% of Python3 online submissions for Binary Tree Vertical Order Traversal
| Memory Usage | 13.8 MB, less than 98.72% of Python3 online submissions for Binary Tree Vertical Order Traversal
| Datastructures | TreeNode
| Algorithms | BFS
| Complexity | Time: O(NlogN) Memory: O(N)

### Procedure

1. ...

### Code

#### Option 1

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def verticalOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        nodes = collections.defaultdict(list)
        queue = collections.deque([(root, 0)])
        while queue:
            node, pos = queue.popleft()
            if not node: continue
            nodes[pos].append(node.val)
            queue += (node.left, pos-1), (node.right, pos+1)
        return [nodes[node] for node in sorted(nodes)]
```

#### Option 2

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def verticalOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        cols = defaultdict(list)
        queue = list()
        if root:
            queue.append((root, 0))
            while queue:
                node, col = queue.pop(0)
                cols[col].append(node.val)
                if node.left:  queue.append((node.left, col - 1))
                if node.right: queue.append((node.right, col + 1))
        return [cols[k] for k in sorted(cols.keys())]
```
