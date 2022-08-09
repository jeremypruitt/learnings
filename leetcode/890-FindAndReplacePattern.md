# 890 - Find and Replace Pattern

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-and-replace-pattern/
| Language | Python 3
| Runtime | 31 ms, faster than 97.04% of Python3 online submissions for Find and Replace Pattern
| Memory Usage | 13.9 MB, less than 81.97% of Python3 online submissions for Find and Replace Pattern
| Datastructures | List[str]
| Algorithms | ??
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

#### Option 1

```python
class Solution:
    def findAndReplacePattern(self, words: List[str], pattern: str) -> List[str]:
        result = []
        for word in words:
            if len(set(word)) != len(set(pattern)): continue
            if len(set(zip(word, pattern))) != len(set(word)): continue
            result.append(word)
        
        return result
```

#### Option 2

```python
class Solution:
    def findAndReplacePattern(self, words: List[str], pattern: str) -> List[str]:
        b = pattern
        def is_iso(a):
            return len(set(a)) == len(set(b)) == len(set(zip(a, b)))
        
        return filter(is_iso, words)
```
