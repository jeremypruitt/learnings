# 1091 - Shortest Path in Binary Matrix

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/shortest-path-in-binary-matrix/
| Language | Python 3
| Runtime | 743 ms, faster than 65.37% of Python3 online submissions for Shortest Path in Binary Matrix
| Memory Usage | 14.4 MB, less than 63.63% of Python3 online submissions for Shortest Path in Binary Matrix
| Datastructures | deque OR list/queue
| Algorithms | BFS (can also use DFS w/ stack)

### Procedure

1. Create queue for next level and add the root node to it
2. BFS - While the queue contains item(s)...
   1. Pop cell/coordinate off the queue
   2. Determine new potential cell for each direction we can travel
      1. Skip if we were to hit a boundary
      2. Skip if we were to hit an invlaid cell (contains a 1)
      3. Return distance if we hit the last row and column
      4. Mark cell as seen and append cell to queue
3. Fail if we hit the end

### Code

```python
class Solution:
    def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
        max_row = len(grid) - 1
        max_col = len(grid[0]) - 1
        
        # Edge cases
        if grid[0][0] != 0 or grid[max_row][max_col] != 0: return -1
        if max_row == 0: return 1
        
        directions = [(1,0),(0,1),(-1,0),(0,-1),(1,1),(1,-1),(-1,1),(-1,-1)]

        queue = [(0,0)]
        distance = 1
        
        while queue:
            distance += 1

            for _ in range(len(queue)):
                x, y = queue.pop(0)
                
                for dirx, diry in directions:
                    # Determine new potential positions
                    row, col = x + dirx, y + diry
                    
                    # Skip this direction if we hit a boundary
                    if not(0 <= row <= max_row and 0 <= col <= max_col): continue
                    
                    # Skip if not a valid cell
                    if grid[row][col] != 0: continue

                    # Return the distance if we hit the last row and column
                    if (row,col) == (max_row, max_col):
                        return distance
                    
                    # Mark as visited and append to queue
                    grid[row][col] = 1
                    queue.append((row,col))
        
        return -1
```
