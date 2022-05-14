# 743 - Network Delay Time

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/network-delay-time/
| Language | Python 3
| Runtime | 480 ms, faster than 88.18% of Python3 online submissions for Network Delay Time
| Memory Usage | 16 MB, less than 76.55% of Python3 online submissions for Network Delay Time

```python
class Solution:
    def networkDelayTime(self, times: List[List[int]], n: int, k: int) -> int:
        graph = defaultdict(list)
        
        for src, dest, time in times:
            graph[src].append((time,dest))
            
        seen = set()
        heap = [(0,k)]
        while heap:
            total_time, node = heapq.heappop(heap)
            
            seen.add(node)
            if len(seen) == n: return total_time
            
            for time, neighbor in graph[node]:
                if neighbor not in seen:
                    heapq.heappush(heap, (total_time+time, neighbor))
            
        return -1
```
