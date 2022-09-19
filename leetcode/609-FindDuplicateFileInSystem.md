# 609 - Find Duplicate File in System

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-duplicate-file-in-system/
| Language | Python 3
| Runtime | 89 ms, faster than 98.47% of Python3 online submissions for Find Duplicate File in System
| Memory Usage | 24 MB, less than 67.80% of Python3 online submissions for Find Duplicate File in System
| Datastructures | List[str], Dict
| Algorithms | Iteration w/ Memoization?
| Complexity | Time: O(NM) Memory: O(N) (N=number of paths, M=keys in groups dict)

### Procedure

1. ...

### Code

```python
class Solution:
    def findDuplicate(self, paths: List[str]) -> List[List[str]]:
        groups = defaultdict(list)
        
        for path in paths:
            dir, *files = path.split()
            
            for file in files:
                name, content = file.split('(')
                groups[content].append(f'{dir}/{name}')
        
        return [g for g in groups.values() if len(g) > 1]
```
