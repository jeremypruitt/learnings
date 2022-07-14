# 510 - Inorder Successor in BST II

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/word-abbreviation/
| Language | Python 3
| Runtime | 142 ms, faster than 29.65% of Python3 online submissions for Inorder Successor in BST II
| Memory Usage | 21.7 MB, less than 13.44% of Python3 online submissions for Inorder Successor in BST II
| Datastructures | Node
| Algorithms | Iteration
| Complexity | Time: O(H) Memory: O(1) (H=Hieght of tree)

### Procedure

1. ...

### Code

```python
class Solution:
    def inorderSuccessor(self, node: 'Node') -> 'Optional[Node]':
        if node.right:
            node = node.right
            while node.left: node = node.left
            return node
        
        while node.parent and node.parent.val < node.val:
            node = node.parent
        
        return node.parent
```
