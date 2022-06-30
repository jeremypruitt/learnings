# 200 - Number of Islands

### Submission A: Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/number-of-islands/
| Language | Python 3
| Runtime | 361 ms, faster than 67.53% of Python3 online submissions for Number of Islands
| Memory Usage | 25.7 MB, less than 7.18% of Python3 online submissions for Number of Islands
| Datastructures | set, matrix
| Algorithms | DFS, recursion

### SubmissionA: Code

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        rows, cols = len(grid), len(grid[0])
        seen = set()
        
        def dfs(row: int, col: int) -> int:
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

### Submission B: Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/number-of-islands/
| Language | Python 3
| Runtime | 442 ms, faster than 55.73% of Python3 online submissions for Number of Islands
| Memory Usage | 16.5 MB, less than 47.88% of Python3 online submissions for Number of Islands
| Datastructures | List[List[str]]
| Algorithms | DFS
| Complexity | Time: O(NM) Memory: O(NM) (N=length of grid, M=height of grid)

### Submission B: Code

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid: return 0
        
        islands = 0
        for i in range( len(grid) ):
            for j in range( len(grid[0]) ):
                if grid[i][j] == '1':
                    islands += 1
                    self.partOfIsland(i,j,grid)
        return islands
    
    def partOfIsland(self,i,j,grid):
        if self.isValidPartOfIsland(i,j,grid): return
        grid[i][j] = '0'
        self.partOfIsland(i,j+1,grid)
        self.partOfIsland(i,j-1,grid)
        self.partOfIsland(i+1,j,grid)
        self.partOfIsland(i-1,j,grid)
    
    def isValidPartOfIsland(self,i,j,grid):
        return (
            i < 0 or
            j < 0 or
            i == len(grid) or
            j == len(grid[0]) or
            grid[i][j] != '1' )
```
