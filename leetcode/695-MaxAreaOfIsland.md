# 695 - Max Area of Island

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/max-area-of-island/
| Language | Python 3
| Runtime | 145 ms, faster than 90.60% of Python3 online submissions for Max Area of Island
| Memory Usage | 16.5 MB, less than 69.88% of Python3 online submissions for Max Area of Island
| Datastructures | List[List[int]]
| Algorithms | DFS w/ recursion
| Complexity | Time: O(NM) Memory: O(1) (N=number of rows,M=number of columns)

### Procedure

1. ...

### Code

```python
class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        rows, cols = len(grid), len(grid[0]) 
        def is_valid_island_cell(row: int, col: int) -> bool:
            if row < 0 or col < 0: return False # Out of bounds
            if row >= rows or col >= cols: return False # Out of bounds
            if grid[row][col] == 0: return False # Reached water
            return True
        
        def get_island_area(row, col):
            if not is_valid_island_cell(row, col): return 0
            
            grid[row][col] = 0 # Mark as water so we ignore it later
            
            # Recursive call to cells around current cell to get area
            up    = get_island_area(row-1, col)
            down  = get_island_area(row+1, col)
            left  = get_island_area(row, col-1)
            right = get_island_area(row, col+1)
            
            return 1 + up + down + left + right # Area of island
        
        area, max_area = 0, 0
        for row in range(rows):
            for column in range(cols):
                area = get_island_area(row, column)
                max_area = max(max_area, area)
        return max_area
```
