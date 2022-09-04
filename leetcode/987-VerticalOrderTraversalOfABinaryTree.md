# 987 - Vertical Order Traversal of a Binary Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/
| Language | Python 3
| Runtime | 64 ms, faster than 24.42% of Python3 online submissions for Vertical Order Traversal of a Binary Tree
| Memory Usage | 14.2 MB, less than 72.74% of Python3 online submissions for Vertical Order Traversal of a Binary Tree
| Datastructures | TreeNode, deque, defaultdict
| Algorithms | BFS? + Memoization
| Complexity | Time: O(NlogN) Memory: O(N)

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
    def verticalTraversal(self, root: Optional[TreeNode]) -> List[List[int]]:
        memo = defaultdict(lambda: defaultdict(lambda: []))
        queue = deque()
        queue.append([root,0,0])
        
        while queue:
            node, row, col = queue.popleft()
            memo[col][row].append(node.val)
            
            if node.left:  queue.append([node.left, row+1,col-1])
            if node.right: queue.append([node.right,row+1,col+1])
        
        output = []
        for col in sorted(memo):
            col_output = []
            for row in memo[col]:
                col_output += sorted(memo[col][row])
            output.append(col_output)
            
        return output
```
