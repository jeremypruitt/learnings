# 200 - Number of Islands

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/number-of-islands/
| Language | Python 3
| Runtime | 361 ms, faster than 67.53% of Python3 online submissions for Number of Islands
| Memory Usage | 25.7 MB, less than 7.18% of Python3 online submissions for Number of Islands
| Datastructures | set, matrix
| Algorithms | DFS, recursion

### Procedure

1. TBD...

### Code

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        rows, cols = len(grid), len(grid[0])
        seen = set()
        
        def dfs(row: int, col: int) -> int:
            #if (0 <= row < rows and 0 <= col < cols and (row,col) not in seen and grid[row][col] == "1"):
            #    seen.add((row,col))
            #    grid[row][col] = "0" # Mark visited
            #    dfs(row+1, col)
            #    dfs(row-1, col)
            #    dfs(row, col+1)
            #    dfs(row, col-1)
            #    return 1
            
            if (row < 0 or row == rows or
                col < 0 or col == cols or
                grid[row][col] == "0"): return 0
            
            seen.add((row,col))
            grid[row][col] = "0" # Mark visited
            
            dfs(row+1, col)
            dfs(row-1, col)
            dfs(row, col+1)
            dfs(row, col-1)

            return 1
        
        number_of_distinct_islands = 0
        for row in range(rows):
            for col in range(cols):
                number_of_distinct_islands += dfs(row, col)
                
        return number_of_distinct_islands
```
