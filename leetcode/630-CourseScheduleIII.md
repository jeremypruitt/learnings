# 630 - Course Schedule III

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/course-schedule-iii/
| Language | Python 3
| Runtime | 1563 ms, faster than 8.47% of Python3 online submissions for Course Schedule III
| Memory Usage | 19.4 MB, less than 90.62% of Python3 online submissions for Course Schedule III
| Datastructures | Heap, List[List[int]
| Algorithms | Greedy + Max Heap
| Complexity | Time: O(NlogN) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def scheduleCourse(self, courses: List[List[int]]) -> int:
        max_heap, start_day = [], 0
        
        for duration, last_day in sorted(courses, key=lambda c: c[1]):
            start_day += duration
            heapq.heappush(max_heap, -duration)
            
            if start_day > last_day:
                new_duration = heapq.heappop(max_heap)
                start_day += new_duration
        
        return len(max_heap)
```
