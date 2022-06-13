# 120 - Triangle

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/triangle/
| Language | Python 3
| Runtime | 112 ms, faster than 32.73% of Python3 online submissions for Triangle
| Memory Usage | 14.9 MB, less than 60.61% of Python3 online submissions for Triangle
| Datastructures | List[List[int]]
| Algorithms | DP (top-down)

### Procedure

1. ...

### Code

#### Option 1: Terse

```python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        for level in range(len(triangle)-2,-1,-1):
            for i in range(level+1):
             triangle[level][i] += min(triangle[level+1][i], triangle[level+1][i+1])
        return triangle[0][0]

```

#### Option 2: Verbose

```python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        m = len(triangle)
        
        # Loop every level in the triangle
        for level in range(1, m):
            # Every level has n elements (n = level). Loop through them
            for i in range(level+1):
                # If you are at the first index at the current level, 
                # you can only add the first element of the previous level
                if i == 0:
                    triangle[level][i] += triangle[level-1][0]
                    
                # If you are at the last index at the current level, 
                # you can only add the last element of the previous level
                elif i == level:
                    triangle[level][i] += triangle[level-1][i-1]
                    
                # For the middle elements
                # You can either add the previous level same index or previous level index - 1
                # Whichever is smaller
                else:
                    triangle[level][i] += min(triangle[level-1][i], triangle[level-1][i-1])
                        
        return min(triangle[-1])
```
