# 32 - Longest Valid Parentheses

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/longest-valid-parentheses/
| Language | Python 3
| Runtime | 64 ms, faster than 46.38% of Python3 online submissions for Longest Valid Parentheses
| Memory Usage | 14 MB, less than 91.05% of Python3 online submissions for Longest Valid Parentheses
| Datastructures | str, int
| Algorithms | loop and count

Runtime: .
Memory Usage: .

### Procedure

1. TBD...

### Code

#### Loop and count, no stack
```python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        left, right = 0, 0
        longest = 0
        
        for char in s:
            if char == "(": left  += 1
            else:           right += 1
                
            if   left == right: longest = max(longest, right*2)
            elif left <  right: left, right = 0, 0
            
        left, right = 0, 0
        for char in reversed(s):
            if char == ")": right += 1
            else:           left  += 1
            
            if   left == right: longest = max(longest, right*2)
            elif left >  right: left, right = 0, 0
        
        return longest
```

#### Stack, no DP
```python
stk, max_len = [(")", -1)], 0
        
for i in range(len(s)):
    if s[i] == ")" and stk[-1][0] == "(":
        stk.pop()
        max_len = max(max_len, i-stk[-1][1])
    else:
        stk.append((s[i], i))
return max_len
```
