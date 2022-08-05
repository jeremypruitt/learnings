# 378 - Kth Smallest Element in a Sorted Matrix

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/
| Language | Python 3
| Runtime | 787 ms, faster than 27.16% of Python3 online submissions for Word Abbreviation
| Memory Usage | 65.2 MB, less than 14.57% of Python3 online submissions for Word Abbreviation
| Datastructures | List[List[int]]
| Algorithms | DFS (postorder)
| Complexity | Time: O(NlogN) Memory: O(M) (C=number of characters in all words in array)

### Procedure

1. ...

### Code

```python
class Solution:
    def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
        rows, cols = len(matrix), len(matrix[0])
        minHeap = []  # val, row, col
        for row in range(min(k, rows)):
            heappush(minHeap, (matrix[row][0], row, 0))

        result = -1  # any dummy value
        for i in range(k):
            result, row, col = heappop(minHeap)
            if col+1 < cols: heappush(minHeap, (matrix[row][col+1], row, col+1))
        
        return result
```
