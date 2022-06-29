# 1229 - Meeting Scheduler

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/meeting-scheduler/
| Language | Python 3
| Runtime | 729 ms, faster than 61.11% of Python3 online submissions for Meeting Scheduler
| Memory Usage | 21.8 MB, less than 12.96% of Python3 online submissions for Meeting Scheduler
| Datastructures | List[List[int]]
| Algorithms | Two Pointers
| Complexity | Time: O(MlogM + NlogN) Memory: O(1) (M=length of slots1, N=length of slots2)

### Procedure

1. ...

### Code

```python
class Solution:
    def minAvailableDuration(self, slots1: List[List[int]], slots2: List[List[int]], duration: int) -> List[int]:
        slots1, slots2 = sorted(slots1), sorted(slots2)
        
        while slots1 and slots2:
            slot1_start = slots1[0][0]
            slot1_end   = slots1[0][1]
            slot2_start = slots2[0][0]
            slot2_end   = slots2[0][1]
            
            # Get min of both ends and max of both starts and
            # check difference vs duration
            def durationFits():
                return min(slot1_end, slot2_end) - max(slot1_start, slot2_start) >= duration
            
            if durationFits():
                return [
                    max(slot1_start, slot2_start),
                    max(slot1_start, slot2_start) + duration ]
            
            if slot1_end < slot2_end:
                slots1.pop(0)
            else:
                slots2.pop(0)
        
        return []
```
