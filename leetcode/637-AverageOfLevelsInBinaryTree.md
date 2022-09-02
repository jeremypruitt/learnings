# 637 - Average of Levels in Binary Tree

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/average-of-levels-in-binary-tree/
| Language | Python 3
| Runtime | 63 ms, faster than 78.53% of Python3 online submissions for Average of Levels in Binary Tree
| Memory Usage | 16.5 MB, less than 87.46% of Python3 online submissions for Average of Levels in Binary Tree
| Datastructures | TreeNode, deque
| Algorithms | BFS
| Complexity | Time: O(N) Space: O(W+H) (W=width of tree, H=height of tree)

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
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        queue, result = deque([root]), []
        
        while queue:
            queue_length, sum_of_level = len(queue), 0
            
            for i in range(queue_length):
                node = queue.popleft()
                sum_of_level += node.val
                if node.left:  queue.append(node.left)
                if node.right: queue.append(node.right)
            
            result.append(sum_of_level / queue_length)

        return result
```
