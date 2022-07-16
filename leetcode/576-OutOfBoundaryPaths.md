# 576 - Out of Boundary Paths

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/out-of-boundary-paths/
| Language | Python 3
| Runtime | 123 ms, faster than 87.98% of Python3 online submissions for Out of Boundary Paths
| Memory Usage | 16.6 MB, less than 70.33% of Python3 online submissions for Out of Boundary Paths
| Datastructures | Dict[set()]
| Algorithms | DP (top-down w/ memoization)
| Complexity | Time: O(Nmn) Memory: O(mn) (N=number of moves available, mn= is size of grid)

### Procedure

1. ...

### Code

```python
class Solution:
    def findPaths(self, m: int, n: int, maxMove: int, startRow: int, startColumn: int) -> int:
        def dfs(x, y, max_move, memo):
            if (x,y,max_move) in memo: return memo[(x,y,max_move)]
            if max_move < 0: return 0
            if x < 0 or x >= m: return 1
            if y < 0 or y >= n: return 1
            
            left  = dfs(x-1, y, max_move-1, memo)
            right = dfs(x+1, y, max_move-1, memo)
            up    = dfs(x, y+1, max_move-1, memo)
            down  = dfs(x, y-1, max_move-1, memo)
            
            memo[(x,y,max_move)] = left + right + up + down
            
            return memo[(x,y,max_move)]
        
        return dfs(startRow,startColumn,maxMove,{}) % (10**9+7)
```
