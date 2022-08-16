# 387 - First Unique Character in a String

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/first-unique-character-in-a-string/
| Language | Python 3
| Runtime | 170 ms, faster than 54.13% of Python3 online submissions for First Unique Character in a String
| Memory Usage | 14.2 MB, less than 59.00% of Python3 online submissions for First Unique Character in a String
| Datastructures | str
| Algorithms | Iteration
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

#### Option 1

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:                    
        d = {}
        for char in s: d[char] = d.get(char, 0) + 1
            
        for i, char in enumerate(s):
            if d[char] == 1: return i
        
        return -1
```

#### Option 2: One-Liner

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:                    
        return min(([s.index(char) for char in set(s) if s.count(char) == 1] or [-1]))
```
