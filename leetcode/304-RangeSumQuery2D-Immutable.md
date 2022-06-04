# 304 - Range Sum Query 2D - Immutable

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/range-sum-query-2d-immutable/
| Language | Python 3
| Runtime | 2384 ms, faster than 36.38% of Python3 online submissions for Range Sum Query 2D - Immutable
| Memory Usage | 25 MB, less than 40.31% of Python3 online submissions for Range Sum Query 2D - Immutable
| Datastructures | List[List[int]]
| Algorithms | DP

### Procedure

1. TBD...

### Code

```python
class NumMatrix:
    def __init__(self, matrix: List[List[int]]):
        if not matrix: return
        num_rows, num_cols = len(matrix), len(matrix[0])
        
        self.dp = [[0 for _ in range(num_cols+1)] for j in range(num_rows+1)]
        
        for i in range(num_rows):
            for j in range(num_cols):
                self.dp[i+1][j+1] = ( matrix[i][j]
                                    + self.dp[i+1][j  ]
                                    + self.dp[i  ][j+1]
                                    - self.dp[i  ][j  ] )

    def sumRegion(self, row1: int, col1: int, row2: int, col2: int) -> int:
        return ( self.dp[row2+1][col2+1]
               - self.dp[row2+1][col1  ]
               - self.dp[row1  ][col2+1]
               + self.dp[row1  ][col1  ] )

# Your NumMatrix object will be instantiated and called as such:
# obj = NumMatrix(matrix)
# param_1 = obj.sumRegion(row1,col1,row2,col2)
```
