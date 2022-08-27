# 363 - Max Sum of Rectangle No Larger Than K

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/
| Language | Python 3
| Runtime | 2309 ms, faster than 89.33% of Python3 online submissions for Max Sum of Rectangle No Larger Than K
| Memory Usage | 15 MB, less than 51.38% of Python3 online submissions for Max Sum of Rectangle No Larger Than K
| Datastructures | List[List[int]]
| Algorithms | Should probably use Kadane's
| Complexity | Time: O(?) Memory: O(?)

### Procedure

1. ...

### Code

```python
class Solution:
    def maxSumSubmatrix(self, matrix: List[List[int]], k: int) -> int:
        m, n = len(matrix), len(matrix[0])
        
		# prefix sum each row
        for row in matrix:
            for i in range(1, n): row[i] = row[i] + row[i-1]
            row.insert(0, 0)
        
        ans = -inf
        for i in range(n):
            for j in range(i, n):
                # init with a 0 in case cur_sum == k at a paricular row
                arr, cur_sum = [0], 0
                
                for r in range(m):
                    # submatrix sum row 0 to r
                    cur_sum += matrix[r][j+1] - matrix[r][i]
                    
                    # search for the best candidate from earlier rows
                    x = bisect_left(arr, cur_sum - k)
                    if x < len(arr):
                        if arr[x] == cur_sum - k: return k
                        else: ans = max(ans, cur_sum - arr[x])
                    
                    # update sorted list of cumulative sums
                    insort(arr, cur_sum)
        
        return ans
```
