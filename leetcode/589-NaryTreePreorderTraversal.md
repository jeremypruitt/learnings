# 589 - N-ary Tree Preorder Traversal

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/n-ary-tree-preorder-traversal/
| Language | Python 3
| Runtime | 46 ms, faster than 98.67% of Python3 online submissions for N-ary Tree Preorder Traversal
| Memory Usage | 16.2 MB, less than 65.03% of Python3 online submissions for N-ary Tree Preorder Traversal
| Datastructures | Node
| Algorithms | DFS
| Complexity | Time: O(V) Memory: O(H) (V=number of vertices, H=height of tree)

### Procedure

1. ...

### Code

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""
class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        output = []
        
        # Depth first search & return output when done
        self.dfs(root,output)
        return output
    
    def dfs(self, root, output):
        # When we reach the bottom, go back up
        if root is None: return
        
        # Add the root val to output
        output.append(root.val)
        
        # Then add children to output
        for child in root.children:
            self.dfs(child,output)
```
