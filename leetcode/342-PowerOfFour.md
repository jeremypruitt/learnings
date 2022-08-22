# 342 - Power of Four

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/power-of-four/
| Language | Python 3
| Runtime | 31 ms, faster than 95.07% of Python3 online submissions for Power of Four
| Memory Usage | 13.8 MB, less than 54.38% of Python3 online submissions for Power of Four
| Datastructures | Int
| Algorithms | Bit Manipulation
| Complexity | Time: O(1) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def isPowerOfFour(self, n: int) -> bool:
        return n > 0 and (n & n-1) == 0 and n & (0xAAAAAAAA) == 0
```
