# Backspace String Compare

Link: https://leetcode.com/problems/backspace-string-compare/
Language: Python 3
Runtime: 41 ms, faster than 60.89% of Python3 online submissions for Backspace String Compare.
Memory Usage: 13.9 MB, less than 23.58% of Python3 online submissions for Backspace String Compare.

```bash
class Solution:
    def backspaceCompare(self, s: str, t: str) -> bool:
        def process(s):
            stack = []
            for char in s:
                if char == "#":
                    if stack: stack.pop()
                else:
                    stack.append(char)
            return stack
        
        return process(s) == process(t)
```
