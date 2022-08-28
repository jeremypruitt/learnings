# 1329 - Sort the Matrix Diagonally

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/sort-the-matrix-diagonally/
| Language | Python 3
| Runtime | 91 ms, faster than 89.03% of Python3 online submissions for Sort the Matrix Diagonally
| Memory Usage | 14.3 MB, less than 76.31% of Python3 online submissions for Sort the Matrix Diagonally
| Datastructures | List[List[int]]
| Algorithms | Memoization
| Complexity | Time: O(MNlogD) Space: O(MN) (M=number of rows, N=number of columns, D is length of diagonal where D=min(M,N))
        

### Procedure

1. ...

### Code

```python
class Solution:
    def diagonalSort(self, mat: List[List[int]]) -> List[List[int]]:
        cols, rows, memo = len(mat), len(mat[0]), defaultdict(list)
        
        for col in range(cols):
            for row in range(rows):
                memo[col-row].append(mat[col][row])
        
        for coordinate in memo:
            memo[coordinate].sort(reverse=1)
        
        for col in range(cols):
            for row in range(rows):
                mat[col][row] = memo[col-row].pop()
        
        return mat
```
