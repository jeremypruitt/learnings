# 354 - Russian Doll Envelopes

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/russian-doll-envelopes/
| Language | Python 3
| Runtime | 1248 ms, faster than 87.12% of Python3 online submissions for Russian Doll Envelopes
| Memory Usage | 61.7 MB, less than 67.37% of Python3 online submissions for Russian Doll Envelopes
| Datastructures | DP, [[int]]
| Algorithms | sort, LIS

### Procedure

1. TBD...

### Code

```python
class Solution:
    def maxEnvelopes(self, envelopes: List[List[int]]) -> int:
        # Sort by width ascending and height descending
        envelopes.sort(key=lambda x: (x[0], -x[1]))

        # Initialize DP array. Prefill our dp table with big
        # numbers, in this way, we can directly update index
        # and not being afraid to out-of-bounds indexes.
        dp = [10**10] * (len(envelopes) + 1)

        for envelope in envelopes:
            dp[bisect_left(dp, envelope[1])] = envelope[1]

        return bisect_left(dp, 10**10)
        # OR:
        #return dp.index(10**10)
```
