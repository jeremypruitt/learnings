# 1383 - Maximum Performance of a Team

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/maximum-performance-of-a-team/
| Language | Python 3
| Runtime | 434 ms, faster than 89.87% of Python3 online submissions for Maximum Performance of a Team
| Memory Usage | 35.6 MB, less than 14.77% of Python3 online submissions for Maximum Performance of a Team
| Datastructures | Min-Heap, List[int]
| Algorithms | Greedy + Min-Heap
| Complexity | Time: O(N(NlogN+logK)) Memory: O(N+K)

### Procedure

1. ...

### Code

```python
class Solution:
    def maxPerformance(self, n: int, speed: List[int], efficiency: List[int], k: int) -> int:
        # Combine speed & efficiency and sort by decreasing efficiency
        people = sorted(zip(speed, efficiency), key=lambda x: -x[1])
        print(people)
        
        result = sum_speed = 0
        min_heap = []
        
        for i, (s,e) in enumerate(people):
            # Push to heap until we have pushed k engineers
            if i < k:
                sum_speed += s
                heapq.heappush(min_heap, s)
            # Once k is reached, if speed bigger than current smallest in heap
            elif s > min_heap[0]:
                sum_speed += s - heapq.heappushpop(min_heap, s)
            else:
                continue
            
            result = max(result, sum_speed * e)
        
        return result % (10**9 + 7)
```
