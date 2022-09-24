# 1680 - Concatenation of Consecutive Binary Numbers

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/concatenation-of-consecutive-binary-numbers/
| Language | Python 3
| Runtime | 1695 ms, faster than 75.97% of Python3 online submissions for Concatenation of Consecutive Binary Numbers
| Memory Usage | 15.9 MB, less than 34.11% of Python3 online submissions for Concatenation of Consecutive Binary Numbers
| Datastructures |int, bin, str
| Algorithms | Binary Conversion + String Concatenation
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def concatenatedBinary(self, n: int) -> int:
        result = ""
        
        for i in range(1,n+1):
            result += format(i,"b")
        
        return int(result,2) % (10**9 + 7)
```
