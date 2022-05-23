# 474 - Ones and Zeroes

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/ones-and-zeroes/
| Language | Python 3
| Runtime | 4817 ms, faster than 35.35% of Python3 online submissions for Ones and Zeroes
| Memory Usage | 14.1 MB, less than 98.50% of Python3 online submissions for Ones and Zeroes
| Datastructures | [[]]
| Algorithms | DP

### Procedure

1. TBD...

### Code

```python
class Solution:
    def findMaxForm(self, strs: List[str], m: int, n: int) -> int:
        dp = [[0 for _ in range(n+1)] for _ in range(m+1)]
        #dp = [[s.count('0'), s.count('1')] for s in strs]
        
        for str in strs:
            zeros, ones = str.count("0"), str.count("1")
            for i in range(m, zeros -1,-1):
                for j in range(n, ones-1, -1):
                    dp[i][j] = max(
                        dp[i][j],
                        dp[i-zeros][j-ones] + 1)
        return dp[m][n]
```
