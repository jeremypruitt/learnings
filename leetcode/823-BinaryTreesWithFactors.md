# 823 - Binary Trees With Factors

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/binary-trees-with-factors/
| Language | Python 3
| Runtime | 496 ms, faster than 76.26% of Python3 online submissions for Binary Trees With Factors
| Memory Usage | 14.1 MB, less than 90.91% of Python3 online submissions for Binary Trees With Factors
| Datastructures | DP
| Algorithms | Group + Least Common Prefix?
| Complexity | Time: O(N^2) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def numFactoredBinaryTrees(self, arr: List[int]) -> int:
        arr.sort()
        dp = {num: 1 for num in arr}
        for i, a in enumerate(arr):
            for b in arr[0:i]:
                if a%b ==0:
                    key = int(a/b)
                    if key in dp:
                        dp[a] += dp[b]*dp[key]

        return sum(dp.values()) % (10**9+7)
```
