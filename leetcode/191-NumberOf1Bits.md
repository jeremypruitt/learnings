# 191 - Number of 1 Bits

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/number-of-1-bits/
| Language | Python 3
| Runtime | 30 ms, faster than 91.85% of Python3 online submissions for Number of 1 Bits
| Memory Usage | 13.8 MB, less than 95.07% of Python3 online submissions for Number of 1 Bits

### Procedure

1. TBD...

### Code

```python
class Solution:
    def hammingWeight(self, n: int) -> int:
        number_of_ones = 0
        while n:
            n &= n - 1
            number_of_ones += 1
        return number_of_ones
```
