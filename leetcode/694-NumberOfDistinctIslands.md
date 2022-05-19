# 694 - Number of Distinct Islands


### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/number-of-distinct-islands/
| Language | Python 3
| Runtime | 254 ms, faster than 68.59% of Python3 online submissions for Number of Distinct Islands
| Memory Usage | 17.8 MB, less than 34.29% of Python3 online submissions for Number of Distinct Islands
| Datastructures | set, matrix
| Algorithms | DFS, recursion

### Procedure

1. TBD...

### Code

```python
class Solution:
    def numDistinctIslands(self, grid: List[List[int]]) -> int:
        rows, cols = len(grid), len(grid[0])
        seen = set()
        signatures = set()
        
        def dfs(row, col, direction):
            nonlocal path
            
            if (0 <= row < rows and 0 <= col < cols and (row,col) not in seen and grid[row][col]):
                seen.add((row,col))
                path += direction
                    
                dfs(row + 1, col, 'D')
                dfs(row - 1, col, 'U')
                dfs(row, col + 1, 'R')
                dfs(row, col - 1, 'L')
                    
                path += 'B'
        
        for row in range(rows):
            for col in range(cols):
                path = ''
                dfs(row, col, 'B')
                if path:
                    signatures.add(path)
        
        return len(signatures)
```
