# 867 - Transpose Matrix

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/transpose-matrix/
| Language | Python 3
| Runtime | 99 ms, faster than 50.08% of Python3 online submissions for Transpose Matrix
| Memory Usage | 14.7 MB, less than 90.58% of Python3 online submissions for Transpose Matrix
| Datastructures | List[List[int]]
| Algorithms | iterate

### Procedure

1. TBD...

### Code

#### Option 1: Easiest to Follow

```python
class Solution:
    def transpose(self, matrix: List[List[int]]) -> List[List[int]]:
        x, y = len(matrix), len(matrix[0])
        transposed = [[None] * x for _ in range(y)]

        for i in range(x):
            for j in range(y):
                transposed[j][i] = matrix[i][j]

        return transposed
```

#### Option 2: Two-Liner

```python
class Solution:
    def transpose(self, matrix: List[List[int]]) -> List[List[int]]:
        x, y = range( len(matrix) ), range( len(matrix[0]) )
        return [[ matrix[i][j] for i in x ] for j in y ]
```

#### Option 3: One-Liner

```python
class Solution:
    def transpose(self, matrix: List[List[int]]) -> List[List[int]]:
      return [[ matrix[i][j] for i,_ in enumerate(matrix) ] for j,_ in enumerate(matrix[0]) ]
        
```
