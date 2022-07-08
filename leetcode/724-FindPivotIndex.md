# 724 - Find Pivot Index

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-pivot-index/
| Language | Python 3
| Runtime | 322 ms, faster than 17.15% of Python3 online submissions for Find Pivot Index
| Memory Usage | 15.3 MB, less than 48.80% of Python3 online submissions for Find Pivot Index
| Datastructures | List[int]
| Algorithms | Iterate / brute-force
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def pivotIndex(self, nums: List[int]) -> int:
        left_sum, total_sum = 0, sum(nums)
        
        for i, num in enumerate(nums):
            if left_sum + num + left_sum == total_sum: return i
            left_sum += num
        
        return -1
```
