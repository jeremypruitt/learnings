# 118 - Pascal's Triangle

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/pascals-triangle/
| Language | Python 3
| Runtime | 61 ms, faster than 16.16% of Python3 online submissions for Pascal's Triangle
| Memory Usage | 13.9 MB, less than 17.88% of Python3 online submissions for Pascal's Triangle
| Datastructures | DP Array
| Algorithms | DP
| Complexity | Time: O(N^2) Memory: O(1) (N=numRows)

### Procedure

1. ...

### Code

```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        result = [[1]*(i+1) for i in range(numRows)]
        for row in range(2, numRows):
            for col in range(1, row):
                result[row][col] = result[row-1][col-1] + result[row-1][col]
        return result
```
