# 334 - Increasing Triplet Subsequence

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/increasing-triplet-subsequence/submissions/
| Language | Python 3
| Runtime | 1634 ms, faster than 15.21% of Python3 online submissions for Increasing Triplet Subsequence
| Memory Usage | 24.6 MB, less than 49.03% of Python3 online submissions for Increasing Triplet Subsequence
| Datastructures | List[str]
| Algorithms | Binary Search?
| Complexity | Time: O(NlogN) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def increasingTriplet(self, nums: List[int]) -> bool:
        first = second = float('inf')
        
        for num in nums:
            if   num <= first:  first  = num
            elif num <= second: second = num
            else: return True
        
        return False
```
