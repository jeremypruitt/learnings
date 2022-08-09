# 729 - My Calendar I

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/my-calendar-i/
| Language | Python 3
| Runtime | 393 ms, faster than 62.19% of Python3 online submissions for My Calendar I
| Memory Usage | 14.6 MB, less than 98.56% of Python3 online submissions for My Calendar I
| Datastructures | List
| Algorithms | Binary Search
| Complexity | Time: O(NlogN) Memory: O(N)

### Procedure

1. ...

### Code

```python
class MyCalendar:
    def __init__(self):
        self.events = []

    def book(self, start: int, end: int) -> bool:
        start_index = bisect.bisect_right(self.events, start)
       
        # Start point must have even index
        if start_index % 2 != 0: return False
        
        end_index = bisect.bisect_left(self.events, end)
        
        # Both start and end must have same index before insertion
        if end_index != start_index: return False
        
        bisect.insort_right(self.events, start)
        bisect.insort_left(self.events, end)
        return True

# Your MyCalendar object will be instantiated and called as such:
# obj = MyCalendar()
# param_1 = obj.book(start,end)
```
