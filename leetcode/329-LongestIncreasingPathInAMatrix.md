# 329 - Longest Increasing Path in a Matrix

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/critical-connections-in-a-network/
| Language | Python 3
| Runtime | 678 ms, faster than 38.81% of Python3 online submissions for Longest Increasing Path in a Matrix
| Memory Usage | 18.2 MB, less than 40.74% of Python3 online submissions for Longest Increasing Path in a Matrix
| Datastructures | hash, matrix
| Algorithms | DFS, recursion

### Procedure

1. TBD...

### Code

```python
class Solution:
    def longestIncreasingPath(self, matrix: List[List[int]]) -> int:
        rows = len(matrix)
        cols = len(matrix[0])
        lip_cache = {} # longest increasing path cache
        
        def dfs(row, col, previous_cell):
            if (row < 0 or row >= rows or
                col < 0 or col >= cols or
                matrix[row][col] <= previous_cell):
                return 0
        
            if (row, col) in lip_cache:
                return lip_cache[(row,col)]
            
            longest = 1
            longest = max(longest, 1 + dfs(row + 1, col, matrix[row][col]))
            longest = max(longest, 1 + dfs(row - 1, col, matrix[row][col]))
            longest = max(longest, 1 + dfs(row, col + 1, matrix[row][col]))
            longest = max(longest, 1 + dfs(row, col - 1, matrix[row][col]))
            
            lip_cache[(row,col)] = longest
            
            return longest
        
        for row in range(rows):
            for col in range(cols):
                dfs(row, col, -237) # Can be any negative int
                
        return max(lip_cache.values())
```
