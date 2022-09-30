# 218 - The Skyline Problem

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/the-skyline-problem/
| Language | Python 3
| Runtime | 160 ms, faster than 81.08% of Python3 online submissions for The Skyline Problem
| Memory Usage | 20 MB, less than 43.32% of Python3 online submissions for The Skyline Problem
| Datastructures | Max Heap
| Algorithms | Max Heap
| Complexity | Time: O(NlogN) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def getSkyline(self, buildings: List[List[int]]) -> List[List[int]]:
        events, heap, result = [], [(0, float("inf"))], [[0, 0]]
        
        # Append start and end of building
        for left, right, height in buildings:
            events.append((left, -height, right))
            events.append((right,      0,     0))

        events.sort()
        
        for position, neg_height, right in events:
            # pop out building which is end
            while heap[0][1] <= position: heapq.heappop(heap)
            
            # If a start of building, push it into heap as current building
            if neg_height != 0: heapq.heappush(heap, (neg_height, right))
            
            # if change in height with previous key point, append to result
            if result[-1][1] != -heap[0][0]: result.append([position, -heap[0][0]])
        
        return result[1:]
```
