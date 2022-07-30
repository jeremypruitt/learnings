# 1074 - Number of Submatrices That Sum to Target

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/
| Language | Python 3
| Runtime | 1110 ms, faster than 77.25% of Python3 online submissions for Number of Submatrices That Sum to Target
| Memory Usage | 15 MB, less than 47.39% of Python3 online submissions for Number of Submatrices That Sum to Target
| Datastructures | List[List[int]]
| Algorithms | ???
| Complexity | Time: O(M^2*N) Memory: O(N) (M=number of rows,N=number of columns)

### Procedure

1. ...

### Code

```python
class Solution:
    def numSubmatrixSumTarget(self, matrix: List[List[int]], target: int) -> int:
        if len(matrix) == 0: return []
        m, n, result = len(matrix), len(matrix[0]), 0
        
        for up in range(m):
            nums = [0] * n
            
            for down in range(up, m):
                mapping = collections.defaultdict(int)
                mapping[0] = 1
                presum = 0
                
                for col in range(n):
                    nums[col] += matrix[down][col]
                    presum += nums[col]
                    result += mapping[presum-target]
                    mapping[presum] += 1
        
        return result
```
