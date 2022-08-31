# 417 - Pacific Atlantic Water Flow

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/pacific-atlantic-water-flow/
| Language | Python 3
| Runtime | 368 ms, faster than 74.02% of Python3 online submissions for Pacific Atlantic Water Flow
| Memory Usage | 15.7 MB, less than 55.20% of Python3 online submissions for Pacific Atlantic Water Flow
| Datastructures | List[List[int]]
| Algorithms | DFS
| Complexity | Time: O(MN) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        if not heights: return []
        p_land, a_land = set(), set()
        rows, cols = len(heights), len(heights[0])
        
        def spread(row, col, land):
            land.add((row, col))
            for x, y in (
                (row+1, col), (row, col+1),
                (row-1, col), (row, col-1)
            ):
                if (
                    0 <= x < rows and
                    0 <= y < cols and
                    heights[x][y] >= heights[row][col] and
                    (x, y) not in land
                ):
                    spread(x, y, land)

        for row in range(rows):
            spread(row,      0, p_land)
            spread(row, cols-1, a_land)
        for col in range(cols):
            spread(0,      col, p_land)
            spread(rows-1, col, a_land)
        
        return list(p_land & a_land)
```
