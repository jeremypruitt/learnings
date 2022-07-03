# 256 - Paint House

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/paint-house/
| Language | Python 3
| Runtime | 73 ms, faster than 76.50% of Python3 online submissions for Pain House
| Memory Usage | 14.1 MB, less than 27.05% of Python3 online submissions for Paint House
| Datastructures | List[List[int]]
| Algorithms | DP
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

#### Option 1

```python
class Solution:
    def minCost(self, costs: List[List[int]]) -> int:
        if not costs: return 0
        
        number_of_houses, number_of_colors = len(costs), len(costs[0])
        range_of_houses, range_of_colors = range(1,number_of_houses), range(number_of_colors)
        
        dp = costs[0]
        for h in range_of_houses:
            pre = dp[:]
            for c in range_of_colors:
                dp[c] = costs[h][c] + min(pre[:c]+pre[c+1:])
        
        return min(dp)
```

#### Option 2

```python
class Solution:
    def minCost(self, costs: List[List[int]]) -> int:
        number_of_houses, number_of_colors = len(costs), len(costs[0])
        range_of_houses, range_of_colors = range(number_of_houses-1,-1,-1), range(number_of_colors)
        
        dp = [[0 for _ in range_of_colors] for _ in range(number_of_houses+1)]
        
        for h in range_of_houses:
            for c in range_of_colors:
                dp[h][c] = costs[h][c] + min(dp[h+1][:c] + dp[h+1][c+1:])
        
        return min(dp[h])
```
