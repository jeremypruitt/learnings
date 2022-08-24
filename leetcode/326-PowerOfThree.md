# 326 - Power of Three

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/power-of-three/
| Language | Python 3
| Runtime | 91 ms, faster than 87.36% of Python3 online submissions for Power of Three
| Memory Usage | 13.9 MB, less than 16.98% of Python3 online submissions for Power of Three
| Datastructures | int
| Algorithms | Math + Integer Limits
| Complexity | Time: O(1) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def isPowerOfThree(self, n: int) -> bool:
        # Can get 1162261467 using any of these:
        #   A) 3 ** 19
        #   B) pow(3, 32)
        return n > 0 and 1162261467 % n == 0
```
