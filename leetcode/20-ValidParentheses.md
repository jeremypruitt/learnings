# 20 - Valid Parentheses

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/valid-parentheses/
| Language | Python 3
| Runtime | 59 ms, faster than 16.02% of Python3 online submissions for Valid Parentheses
| Memory Usage | 13.9 MB, less than 24.44% of Python3 online submissions for Valid Parentheses
| Datastructures | stack
| Algorithms | iterator

### Procedure

1. TBD...

### Code

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        map = { ')':'(', '}':'{', ']':'[' }
        
        for char in s:
            if char in map:
                if stack and stack[-1] == map[char]:
                    stack.pop()
                else:
                    return False
            else:
                stack.append(char)
                
        return not stack
```
