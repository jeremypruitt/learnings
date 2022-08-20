# 871 - Minimum Number of Refueling Stops

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/minimum-number-of-refueling-stops/
| Language | Python 3
| Runtime | 787 ms, faster than 27.16% of Python3 online submissions for Word Abbreviation
| Memory Usage | 65.2 MB, less than 14.57% of Python3 online submissions for Word Abbreviation
| Datastructures | Heap, List[List[int]]
| Algorithms | Greedy Heap
| Complexity | Time: O(NlogN) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def minRefuelStops(self, target: int, startFuel: int, stations: List[List[int]]) -> int:
        s = [(0, 0)] + stations + [(target, 0)]
        heap, min_stops = [], 0
        
        for i in range(1, len(s)):
            startFuel -= s[i][0] - s[i-1][0]
            
            while heap and startFuel < 0:
                startFuel -= heappop(heap)
                min_stops += 1
            
            if startFuel < 0:
                return -1
            
            heappush(heap, -s[i][1])
            
        return min_stops
```
