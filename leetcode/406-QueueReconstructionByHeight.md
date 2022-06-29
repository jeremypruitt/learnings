# 406 - Queue Reconstruction by Height

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/queue-reconstruction-by-height/
| Language | Python 3
| Runtime | 135 ms, faster than 66.19% of Python3 online submissions for Queue Reconstruction by Height
| Memory Usage | 14.4 MB, less than 93.98% of Python3 online submissions for Queue Reconstruction by Height
| Datastructures | List[List[int]]
| Algorithms | Greedy
| Complexity | Time: O(N^2) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def reconstructQueue(self, people: List[List[int]]) -> List[List[int]]:
        people.sort(key = lambda p: (-p[0], p[1]))
        result = []
        for p in people: result.insert(p[1], p)
        return result
```
