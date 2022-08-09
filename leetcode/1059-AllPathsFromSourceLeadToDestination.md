# 1059 - All Paths from Source Lead to Destination

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/all-paths-from-source-lead-to-destination/
| Language | Python 3
| Runtime | 399 ms, faster than 61.28% of Python3 online submissions for All Paths from Source Lead to Destination
| Memory Usage | 19.6 MB, less than 43.25% of Python3 online submissions for All Paths from Source Lead to Destination
| Datastructures | List[List[int]]
| Algorithms | DFS (preorder w/ recursion)
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def leadsToDestination(self, n: int, edges: List[List[int]], source: int, destination: int) -> bool:
        graph = defaultdict(list)
        for a, b in edges: graph[a].append(b)
        
        # if there exist paths from destination,
        # then no paths end in destination
        if len(graph[destination]) > 0: return False
        
        def dfs(node: int = source) -> bool:
            # Arrived at or can reach destination
            if node == destination or graph[node] == True: return True
            
            # Found a cycle or at leaf that is not destination
            if graph[node] == False or len(graph[node]) == 0:  return False
            
            nodes_to_visit = graph[node]
            graph[node] = False
            
            # If all nodes we can get to from node can get to
            # destination without looping
            if all(dfs(child) for child in nodes_to_visit):
                graph[node] = True
                return True
            
            return False
            
        return dfs()
```
