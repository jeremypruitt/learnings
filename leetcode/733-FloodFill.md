# 733 - Flood Fill

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/flood-fill/
| Language | Python 3
| Runtime | 87 ms, faster than 79.09% of Python3 online submissions for Flood Fill
| Memory Usage | 14.2 MB, less than 37.62% of Python3 online submissions for Flood Fill
| Datastructures | List[List[int]]
| Algorithms | DFS
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, new_color: int) -> List[List[int]]:
        rows, cols = len(image), len(image[0])
        color = image[sr][sc]
        
        def isNotValidPixel(row,col):
            return (
                row < 0 or row >= rows or
                col < 0 or col >= cols )
        
        def isNotValidColor(row,col):
            return (
                image[row][col] == new_color or
                image[row][col] != color )
        
        def dfs(row,col):
            if isNotValidPixel(row,col): return
            if isNotValidColor(row,col): return
            
            image[row][col] = new_color
            dfs(row+1,col)
            dfs(row-1,col)
            dfs(row,col+1)
            dfs(row,col-1)
        
        dfs(sr,sc)
        return image
```
