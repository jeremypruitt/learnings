# 746 - Min Cost Climbing Stairs

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/min-cost-climbing-stairs/
| Language | Python 3
| Runtime | 120 ms, faster than 16.08% of Python3 online submissions for Min Cost Climbing Stairs
| Memory Usage | 14.1 MB, less than 20.20% of Python3 online submissions for Min Cost Climbing Stairs
| Datastructures | List[int]
| Algorithms | DP (tabulation w/ iteration)
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        if not cost: return 0
        
        for i in range(2, len(cost)): cost[i] += min(cost[i-1],cost[i-2])
        return min(cost[-1],cost[-2])
        
        n = len(cost)
        dp = [0] * (n+1) # dp[i] is min cost to reach floor i
        for i in range(2,n+1):
            jump_one = dp[i-1] + cost[i-1]
            jump_two = dp[i-2] + cost[i-2]
            dp[i] = min(jump_one,jump_two)
        return dp[n]
```
