# 392 - Is Subsequence

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/is-subsequence/
| Language | Python 3
| Runtime | 61 ms, faster than 25.59% of Python3 online submissions for Is Subsequence
| Memory Usage | 13.9 MB, less than 45.38% of Python3 online submissions for Is Subsequence
| Datastructures | str
| Algorithms | 2 Pointers
| Complexity | Time: O(T), Space: O(1) (T=length of target length)

### Procedure

1. ...

### Code

```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        if len(s) == 0: return True
        s_ptr = 0
        for t_ptr in range(len(t)):
            if s[s_ptr] == t[t_ptr]:
                s_ptr += 1
                if s_ptr == len(s): return True
```
