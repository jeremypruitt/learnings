# 376 - Wiggle Subsequence

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/wiggle-subsequence/
| Language | Python 3
| Runtime | 55 ms, faster than 53.05% of Python3 online submissions for Wiggle Subsequence
| Memory Usage | 13.9 MB, less than 77.55% of Python3 online submissions for Wiggle Subsequence
| Datastructures | List[int]
| Algorithms | Greedy w/ Flag
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def wiggleMaxLength(self, nums: List[int]) -> int:
        if not nums: return 0
        
        length, up = 1, None
        
        for i in range(1, len(nums)):
            if nums[i] > nums[i-1] and up != True:  length += 1; up = True
            if nums[i] < nums[i-1] and up != False: length += 1; up = False
        return length
```
