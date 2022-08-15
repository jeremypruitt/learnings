# 13 - Roman to Integer

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/roman-to-integer/
| Language | Python 3
| Runtime | 40 ms, faster than 99.04% of Python3 online submissions for Roman to Integer
| Memory Usage | 13.8 MB, less than 76.66% of Python3 online submissions for Roman to Integer
| Datastructures | str
| Algorithms | Iteration
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

#### Option 1

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        symbols = {
            'I':    1, 'V':   5,
            'X':   10, 'L':  50,
            'C':  100, 'D': 500,
            'M': 1000 }
        
        answer = 0
        s = s.replace("IV", "IIII").replace("IX", "VIIII")
        s = s.replace("XL", "XXXX").replace("XC", "LXXXX")
        s = s.replace("CD", "CCCC").replace("CM", "DCCCC")
        return sum([symbols[char] for char in s])
```

#### Option 2

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        symbols = {
            'I':    1, 'V':   5,
            'X':   10, 'L':  50,
            'C':  100, 'D': 500,
            'M': 1000 }
        
        answer = 0
        for i, char in enumerate(s[:-1]):
            next_char = s[i+1]
            if symbols[char] < symbols[next_char]:
                answer -= symbols[char]
            else:
                answer += symbols[char]
        last_char = s[-1]
        answer += symbols[last_char]
        return answer
```
