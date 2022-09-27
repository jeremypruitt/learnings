# 838 - Push Dominoes

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/push-dominoes/
| Language | Python 3
| Runtime | 462 ms, faster than 65.19% of Python3 online submissions for Push Dominoes
| Memory Usage | 15.5 MB, less than 95.79% of Python3 online submissions for Push Dominoes
| Datastructures | str, int
| Algorithms | Two-Pointers
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def pushDominoes(self, dominoes: str) -> str:
        dominoes = 'L' + dominoes + 'R'
        result, left = "", 0
        
        for right in range(1, len(dominoes)):
            if dominoes[right] == '.': continue
            
            if left: result += dominoes[left]
            
            middle = right - left - 1
            if dominoes[left] == dominoes[right]:
                result += dominoes[left] * middle
            elif dominoes[left] == 'L' and dominoes[right] == 'R':
                result += '.' * middle
            else:
                result += 'R' * (middle // 2) + '.' * (middle % 2) + 'L' * (middle // 2)
            
            left = right
        
        return result
```
