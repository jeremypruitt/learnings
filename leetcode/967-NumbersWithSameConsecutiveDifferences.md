# 967 - Numbers With Same Consecutive Differences

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/numbers-with-same-consecutive-differences/
| Language | Python 3
| Runtime | 48 ms, faster than 85.71% of Python3 online submissions for Numbers With Same Consecutive Differences
| Memory Usage | 14.3 MB, less than 21.77% of Python3 online submissions for Numbers With Same Consecutive Differences
| Datastructures | List[int]
| Algorithms | DFS
| Complexity | Time: O(2^N) Memory: O(2^N)

### Procedure

1. ...

### Code

```python
class Solution:
    def numsSameConsecDiff(self, n: int, k: int) -> List[int]:
        if n == 1: return list(range(10))
        if k == 0: return [str(i)*n for i in range(1, 10)]
        
        result = []
        
        def dfs(path):
            if n == 0:
                return ans.append(path)
            if len(path) == n:
                result.append( int(''.join(map(str, path))) )
                return 
            
            next_num = path[-1] + k
            if next_num < 10: dfs(path+[next_num])
                
            next_num = path[-1] - k
            if next_num >= 0: dfs(path+[next_num])
        
        for i in range(1, 10): dfs([i])
            
        return result
```
