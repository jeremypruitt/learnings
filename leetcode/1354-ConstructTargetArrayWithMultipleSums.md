# 1354 - Construct Target Array With Multiple Sums

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/construct-target-array-with-multiple-sums/
| Language | Python 3
| Runtime | 428 ms, faster than 45.88% of Python3 online submissions for Construct Target Array With Multiple Sums
| Memory Usage | 20 MB, less than 25.88% of Python3 online submissions for Construct Target Array With Multiple Sums
| Datastructures | Max-Heap
| Algorithms | Working Backwards?
| Complexity | Time: O(NlogKlogN) Memory: O(m)

### Procedure

1. ...

### Code

```python
class Solution:
    def isPossible(self, target: List[int]) -> bool:
        total = sum(target)
        
        # Negate nums to use min-heap as max-heap
        target = [-num for num in target]
        heapq.heapify(target)
        
        while abs(target[0]) != 1:
            largest = -target[0]
            total -= largest
            
            if largest == 1 or total == 1:
                return True
            if largest < total or total == 0 or largest % total == 0:
                return False
            
            largest %= total
            total += largest
            heapq.heapreplace(target, -largest)
        
        return True
```
