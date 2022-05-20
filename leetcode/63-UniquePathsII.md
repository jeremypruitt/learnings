# 63 - Unique Paths II

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/unique-paths-ii/
| Language | Python 3
| Runtime | 45 ms, faster than 82.85% of Python3 online submissions for Unique Paths II
| Memory Usage | 14.2 MB, less than 19.70% of Python3 online submissions for Unique Paths II
| Datastructures | set, matrix
| Algorithms | DFS, recursion

### Procedure

1. TBD...

### Code

```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        rows, cols = len(obstacleGrid), len(obstacleGrid[0])
        seen = {}
        
        if obstacleGrid[rows-1][cols-1] == 1:
            return 0
        
        def dfs(row: int, col: int) -> int:
            if (row, col) == (rows - 1, cols - 1):
                return 1
            
            if row >= rows or col >= cols or obstacleGrid[row][col] == 1:
                return 0
            
            if (row, col) in seen:
                return seen[(row,col)]
            
            seen[(row,col)] = dfs(row+1, col) + dfs(row, col+1)
            
            return seen[(row,col)]
        
        return dfs(0,0)
```
