# 629 - K Inverse Pairs Array

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/k-inverse-pairs-array/
| Language | Python 3
| Runtime | 457 ms, faster than 88.75% of Python3 online submissions for K Inverse Pairs Array
| Memory Usage | 14.2 MB, less than 72.50% of Python3 online submissions for K Inverse Pairs Array
| Datastructures | List/Table
| Algorithms | DP (bottom up w/ tabulation)
| Complexity | Time: O(nk) Memory: O(k)

### Procedure

1. ...

### Code

```python
class Solution:
    def kInversePairs(self, n: int, k: int) -> int:
        table = [1] + [0] * k
        for i in range(2, n+1):
            for j in range(1, k + 1): table[j] += table[j-1]
            for j in range(k, 0, -1): table[j] -= j - i >= 0 and table[j-i]
        return table[k] % (10**9+7)
```
