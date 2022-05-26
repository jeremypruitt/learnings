# 277 - Find the Celebrity

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-the-celebrity/
| Language | Python 3
| Runtime | 2526 ms, faster than 11.92% of Python3 online submissions for Find the Celebrity
| Memory Usage | 14.1 MB, less than 60.00% of Python3 online submissions for Find the Celebrity

### Procedure

1. TBD...

### Code

```python
# The knows API is already defined for you.
# return a bool, whether a knows b
# def knows(a: int, b: int) -> bool:
class Solution:
    def findCelebrity(self, n: int) -> int:
        candidate = 0
        
        for i in range(1,n):
            if knows(candidate,i):
                candidate = i
                
        for i in range(candidate):
            if knows(candidate, i) or not knows(i, candidate):
                return -1
        
        for i in range(candidate + 1, n):
            if not knows(i, candidate):
                return -1
            
        return candidate
```
