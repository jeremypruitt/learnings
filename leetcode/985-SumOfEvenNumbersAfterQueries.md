# 985 - Sum of Even Numbers After Queries

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/sum-of-even-numbers-after-queries/
| Language | Python 3
| Runtime | 1248 ms, faster than 13.52% of Python3 online submissions for Sum of Even Numbers After Queries
| Memory Usage | 20.5 MB, less than 75.51% of Python3 online submissions for Sum of Even Numbers After Queries
| Datastructures | List[List[int]]
| Algorithms | Iteration w/ Even/Odd Analysis?
| Complexity | Time: O(M+N) Memory: O(N) (N=length of nums, M=length of queries)

### Procedure

1. ...

### Code

```python
class Solution:
    def sumEvenAfterQueries(self, nums: List[int], queries: List[List[int]]) -> List[int]:
        even_sum = sum(num for num in nums if num % 2 == 0)
        result: list[int] = []
        
        for value, i in queries:
            if nums[i] % 2 == 0: even_sum -= nums[i]
            
            nums[i] += value
            
            if nums[i] % 2 == 0: even_sum += nums[i]
            
            result.append(even_sum)
        
        return result
```
