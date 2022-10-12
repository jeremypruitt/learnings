# 976 - Largest Perimeter Triangle

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/largest-perimeter-triangle/submissions/
| Language | Python 3
| Runtime | 192 ms, faster than 98.62% of Python3 online submissions for Largest Perimeter Triangle
| Memory Usage | 15.4 MB, less than 91.63% of Python3 online submissions for Largest Perimeter Triangle
| Datastructures | List[int]
| Algorithms | Sort + Iteration?
| Complexity | Time: O(ClogC) Memory: O(C) (C=number of characters in all words in array)

### Procedure

1. ...

### Code

```python
class Solution:
    def largestPerimeter(self, nums: List[int]) -> int:
        nums = sorted(nums, reverse=True)
        
        for i in range(len(nums) - 2):
            if nums[i] < nums[i+1] + nums[i+2]:
                return nums[i] + nums[i+1] + nums[i+2]
        
        return 0
```
