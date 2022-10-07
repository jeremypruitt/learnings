# 732 - My Calendar III

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/my-calendar-iii/submissions/
| Language | Python 3
| Runtime | 1030 ms, faster than 82.77% of Python3 online submissions for My Calendar III
| Memory Usage | 20.1 MB, less than 11.38% of Python3 online submissions for My Calendar III
| Datastructures | defaultdict
| Algorithms | Segment Tree
| Complexity | Time: O(1) Memory: O(1)

### Procedure

1. ...

### Code

```python
class MyCalendarThree:
    def __init__(self):
        self.seg  = defaultdict(int)
        self.lazy = defaultdict(int)

    def book(self, start: int, end: int) -> int:
        def update(start, end, left = 0, right = 10**9, ID = 1):
            if right <= start or end <= left: return 
            if start <= left < right <= end:
                self.seg[ID] += 1
                self.lazy[ID] += 1
            else:
                mid = (left + right) // 2
                update(start, end, left, mid,   2 * ID)
                update(start, end, mid,  right, 2 * ID+1)
                self.seg[ID] = self.lazy[ID] + max(self.seg[2*ID], self.seg[2*ID+1])
        
        update(start, end)
        
        return self.seg[1]
```
