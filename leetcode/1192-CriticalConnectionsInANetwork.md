# 1192 - Critical Connections in a Network

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/critical-connections-in-a-network/
| Language | Python 3
| Runtime | 2657 ms, faster than 68.76% of Python3 online submissions for Critical Connections in a Network
| Memory Usage | 80.4 MB, less than 38.90% of Python3 online submissions for Critical Connections in a Network
| Datastructures | stack
| Algorithms | Tarjan, recursion

### Procedure

1. TBD...

### Code

```python
class Solution:
    def criticalConnections(self, n: int, connections: List[List[int]]) -> List[List[int]]:
        adjacency = defaultdict(list)
        for node1, node2 in connections:
            adjacency[node1].append(node2)
            adjacency[node2].append(node1)
            
        dfs_number = defaultdict(int)
        oldest_reachable = defaultdict(int)
        critical_connections = []
        timestamp = 0
        
        def tarjan(node, parent, adjacency, connections, timestamp, oldest_reachable):
            timestamp += 1
            dfs_number[node] = timestamp
            oldest_reachable[node] = timestamp
            
            for neighbor in adjacency[node]:
                if neighbor == parent: continue
                if not dfs_number[neighbor]:
                    tarjan(neighbor, node, adjacency, connections, timestamp, oldest_reachable)
                
                oldest_reachable[node] = min(oldest_reachable[node], oldest_reachable[neighbor])
                
                if oldest_reachable[neighbor] > dfs_number[node]: connections.append([node,neighbor])
                    
        tarjan(0, None, adjacency, critical_connections, 1, oldest_reachable)
        
        return critical_connections
```
