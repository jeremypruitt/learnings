# 205 - Isomorphic Strings

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/isomorphic-strings/
| Language | Python 3
| Runtime | 68 ms, faster than 38.69% of Python3 online submissions for Isomorphic Strings
| Memory Usage | 14.1 MB, less than 87.87% of Python3 online submissions for Isomorphic Strings
| Datastructures | Cache (seen hash)
| Algorithms | 2 Dicts
| Complexity | Time: O(n), Space: O(26)

### Procedure

1. ...

### Code

```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        def is_mismatch():
            if (
                (s_char not in s_cache) or (s_cache[s_char] != t_char) or
                (t_char not in t_cache) or (t_cache[t_char] != s_char)
               ): return True
        
        s_cache = {}
        t_cache = {}
        
        for s_char, t_char in zip(s,t):
            if s_char not in s_cache and t_char not in t_cache:
                s_cache[s_char] = t_char
                t_cache[t_char] = s_char
            
            if is_mismatch():
                return False
        
        return True
```
