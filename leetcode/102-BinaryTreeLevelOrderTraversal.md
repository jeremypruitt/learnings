# 102 - Binary Tree Level Order Traversal

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/binary-tree-level-order-traversal/
| Language | Python 3, Go
| Runtime | 49 ms, faster than 57.85% of Python3 online submissions for Binary Tree Level Order Traversal
| Memory Usage | 14.2 MB, less than 50.88% of Python3 online submissions for Binary Tree Level Order Traversal
| Datastructures | Queue, TreeNode, List[List[int]]
| Algorithms | BFS

### Procedure

1. Create our answer List and our queue to use for each level. Add root to queue
2. Loop until queue is empty. Create new level array each level of tree.
3. As many times as the length of the queue, check if current node not null.
4. If current not null add it to the level list and add left and right of the current to the queue.
5. Append each level array in the answer array each iteration (if its not empty)

### Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root: return None
        if not root.left and not root.right: return [[root.val]]
        result = []
        queue = deque()
        queue.append(root)
        
        while queue:
            level = []
            for _ in range( len(queue) ):
                current = queue.popleft()
                if (current):
                    level.append(current.val)
                    queue.append(current.left)
                    queue.append(current.right)
            
            if level: result.append(level)
        return result
```

```go
func levelOrder(root *TreeNode) [][]int {
    var result [][]int
    
    customLevelOrder(root, &result, 0)
    
    return result
}

func customLevelOrder(root *TreeNode, preResult *[][]int, level int){
    if root == nil {
        return
    }
    
    if len(*preResult) == level {
        *preResult = append(*preResult, []int{})
    }
    
    (*preResult)[level] = append((*preResult)[level], root.Val)
    
    customLevelOrder(root.Left, preResult, level + 1)
    customLevelOrder(root.Right, preResult, level + 1)
}
```
