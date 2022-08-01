# 62 - Unique Paths

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/unique-paths/
| Language | Python 3
| Runtime | 40 ms, faster than 76.07% of Python3 online submissions for Unique Paths
| Memory Usage | 13.9 MB, less than 73.95% of Python3 online submissions for Unique Paths
| Datastructures | List[int]
| Algorithms | DP
| Complexity | Time: O(N*M) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        # Start by creating the bottom row. The
        # bottom row should be all 1s as there is
        # only one way to get to the bottom right.
        row = [1] * n
        
        for _ in range(m-1):
            new_row = [1] * n
            for col in range(n-2, -1, -1):
                new_row[col] = new_row[col+1] + row[col]
            row = new_row
        
        return row[0]
```
