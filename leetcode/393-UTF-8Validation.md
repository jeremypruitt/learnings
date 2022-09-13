# 393 - UTF-8 Validation

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/utf-8-validation/submissions/
| Language | Python 3
| Runtime | 148 ms, faster than 76.75% of Python3 online submissions for UTF-8 Validation
| Memory Usage | 14.2 MB, less than 70.76% of Python3 online submissions for UTF-8 Validation
| Datastructures | List[int]
| Algorithms | String Manipulation
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def validUtf8(self, data: List[int]) -> bool:
        count = 0
        
        for byte in data:
            if byte >= 128 and byte <= 191:
                if not count:  return False
                count -= 1
            else:
                if count: return False
                if   byte < 128: continue
                elif byte < 224: count = 1
                elif byte < 240: count = 2
                elif byte < 248: count = 3
                else: return False
                    
        return count == 0
```
