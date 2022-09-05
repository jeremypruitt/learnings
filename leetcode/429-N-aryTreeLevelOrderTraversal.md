# 429 - N-ary Tree Level Order Traversal

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/n-ary-tree-level-order-traversal/
| Language | Python 3
| Runtime | 60 ms, faster than 83.32% of Python3 online submissions for N-ary Tree Level Order Traversal
| Memory Usage | 16.1 MB, less than 50.08% of Python3 online submissions for N-ary Tree Level Order Traversal
| Datastructures | Node, deque
| Algorithms | BFS
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

#### Option 1: Verbose

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""
class Solution:
    def levelOrder(self, root: 'Node') -> List[List[int]]:
        if not root: return None
        Q, result = deque([root]), []
        
        while Q:
            level = []
            for _ in range(len(Q)):
                node = Q.popleft()
                level.append(node.val)
                for child in node.children: Q.append(child)
            
            result.append(level)
        
        return result
```

#### Option 1: Terse

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""
class Solution:
    def levelOrder(self, root: 'Node') -> List[List[int]]:
        if not root: return []
        Q, result = deque([root]), []
        while Q:
            result.append([node.val for node in Q])
            Q = [child for node in Q for child in node.children]
        
        return result
```
