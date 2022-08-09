# 377 - Combination Sum IV

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/combination-sum-iv/
| Language | Python 3
| Runtime | 53 ms, faster than 72.51% of Python3 online submissions for Combination Sum IV
| Memory Usage | 13.8 MB, less than 80.97% of Python3 online submissions for Combination Sum IV
| Datastructures | DP array, List[int]
| Algorithms | DP (tabulation w/ iteration)
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def combinationSum4(self, nums: List[int], target: int) -> int:
        nums, dp = sorted(nums), [1] + [0] * (target)
        for i in range(target+1):
            for num in nums:
                if num  > i: break
                if num == i: dp[i] += 1
                if num  < i: dp[i] += dp[i-num]
        return dp[target]
```
