# 1197 - Minimum Knight Moves

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/minimum-knight-moves/
| Language | Python 3
| Runtime | 85 ms, faster than 84.29% of Python3 online submissions for Minimum Knight Moves
| Memory Usage | 14 MB, less than 98.25% of Python3 online submissions for Minimum Knight Moves
| Datastructures | queue
| Algorithms | BFS, Greedy

### Procedure

1. TBD...

### Code

```python
class Solution:
    def minKnightMoves(self, x: int, y: int) -> int:
        x, y = abs(x), abs(y)
        result = 0
        while x > 4 or y > 4:
            result += 1
            if x >= y:
                x -= 2
                y -= 1 if y >= 1 else -1
            else:
                x -= 1 if x >= 1 else -1
                y -= 2
        
        moves = ((2,1), (1,2), (-1,2), (-2,1), (-2,-1), (-1,-2), (1,-2), (2,-1))
        queue = collections.deque([(0,0,0)])
        
        while queue:
            i, j, steps = queue.popleft()
            if i == x and j ==y:
                return result + steps
            for di, dj in moves:
                if (x-i) * di > 0 or (y-j) * dj > 0:
                    queue.append((i+di, j+dj, steps + 1))
```
