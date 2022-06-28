# 1647 - Minimum Deletions to Make Character Frequencies Unique

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/minimum-deletions-to-make-character-frequencies-unique/
| Language | Python 3
| Runtime | 133 ms, faster than 91.66% of Python3 online submissions for Minimum Deletions to Make Character Frequencies Unique
| Memory Usage | 14.9 MB, less than 51.90% of Python3 online submissions for Minimum Deletions to Make Character Frequencies Unique
| Datastructures | set, dict
| Algorithms | Counter & decrement until unique
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def minDeletions(self, s: str) -> int:
        result, count, cache = 0, Counter(s), set()
        
        for value in count.values():
            while value in cache and value > 0:
                value  -= 1
                result += 1
            
            cache.add(value)
        
        return result
```
