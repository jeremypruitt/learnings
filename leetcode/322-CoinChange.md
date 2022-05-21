# 322 - Coin Change

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/coin-change/
| Language | Python 3
| Runtime | 2012 ms, faster than 45.85% of Python3 online submissions for Coin Change
| Memory Usage | 14.1 MB, less than 82.65% of Python3 online submissions for Coin Change
| Datastructures | list
| Algorithms | DP

### Procedure

1. TBD...

### Code

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [amount+1] * (amount+1)
        dp[0] = 0
        
        for amount in range(1, amount+1):
            for coin in coins:
                if amount - coin >= 0:
                    dp[amount] = min(dp[amount], 1 + dp[amount-coin])
        
        if dp[amount] != amount + 1:
            return dp[amount]
        else:
            return -1
```
