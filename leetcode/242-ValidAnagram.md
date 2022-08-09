# 242 - Valid Anagram

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/valid-anagram/
| Language | Python 3
| Runtime | 101 ms, faster than 18.99% of Python3 online submissions for Valid Anagram
| Memory Usage | 14.5 MB, less than 67.19% of Python3 online submissions for Valid Anagram
| Datastructures | Counter
| Algorithms | Group + Least Common Prefix?
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t): return False
        
        count_s, count_t = {}, {}
        
        for i in range(len(s)):
            count_s[ s[i] ] = 1 + count_s.get(s[i],0)
            count_t[ t[i] ] = 1 + count_t.get(t[i],0)
        
        for c in count_s:
            if count_s[c] != count_t.get(c,0): return False
        
        return True
```
