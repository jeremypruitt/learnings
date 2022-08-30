# 48 - Rotate Image

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/rotate-image/
| Language | Python 3
| Runtime | 58 ms, faster than 44.09% of Python3 online submissions for Rotate Image
| Memory Usage | 13.9 MB, less than 29.99% of Python3 online submissions for Rotate Image
| Datastructures | List[List[int]]
| Algorithms | Flip-Flip?
| Complexity | Time: O(M) Memory: O(1)

### Procedure

1. ...

### Code

#### Option 1

```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        matrix.reverse()
        for i in range(len(matrix)):
            for j in range(i):
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
```

#### Option 2: One-Liner

```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        matrix[::] = zip(*matrix[::-1])
```

#### Option 3

```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        length = len(matrix)
        for i in range(length):
            for j in range(i+1,length):
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
        
        for row in matrix: row.reverse()
```
