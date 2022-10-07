# 981 - Time Based Key-Value Store

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/time-based-key-value-store/submissions/
| Language | Python 3
| Runtime | 774 ms, faster than 93.56% of Python3 online submissions for Time Based Key-Value Store
| Memory Usage | 71.9 MB, less than 52.20% of Python3 online submissions for Time Based Key-Value Store
| Datastructures | List[str]
| Algorithms | Binary Search
| Complexity | Time: O(set=N,get=logN) Memory: O(1)

### Procedure

1. ...

### Code

```python
class TimeMap:
    def __init__(self):
        self.dic = collections.defaultdict(list)

    def set(self, key: str, value: str, timestamp: int) -> None:
        self.dic[key].append([timestamp, value])

    def get(self, key: str, timestamp: int) -> str:
        vals = self.dic[key]
        left, right = 0, len(vals)
        
        while left < right:
            mid = (left + right) // 2
            if   vals[mid][0] <= timestamp: left  = mid + 1
            elif vals[mid][0] >  timestamp: right = mid
        
        return "" if right == 0 else vals[right - 1][1]
```
