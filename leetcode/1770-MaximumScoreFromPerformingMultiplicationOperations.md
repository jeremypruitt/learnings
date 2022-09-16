# 1770 - Maximum Score from Performing Multiplication Operations

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/maximum-score-from-performing-multiplication-operations/
| Language | Python 3
| Runtime | 8488 ms, faster than 34.52% of Python3 online submissions for Maximum Score from Performing Multiplication Operations
| Memory Usage | 22.7 MB, less than 98.11% of Python3 online submissions for Maximum Score from Performing Multiplication Operations
| Datastructures | DP Table
| Algorithms | DP - Bottom-Up w/ Tabulation
| Complexity | Time: O(M^2) Memory: O(M^2) (C=number of characters in all words in array)

### Procedure

1. ...

### Code

```python
class Solution:
    def maximumScore(self, nums: List[int], multipliers: List[int]) -> int:
        n, m = len(nums), len(multipliers)
        dp = [0] * (m+1)
        
        for i in range(1,m+1):
            multiplier = multipliers[i-1]
            dp[i] = dp[i-1] + multiplier*nums[i-1]
            
            for left in reversed(range(1,i)):
                dp[left] = max(
                    dp[left]   + multiplier * nums[n - (i - left)],
                    dp[left-1] + multiplier * nums[left-1])
            
            dp[0] = dp[0] + multiplier * nums[n-i]
        
        return max(dp)
```
