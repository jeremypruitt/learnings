# 215 - Kth Largest Element in an Array

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/kth-largest-element-in-an-array/
| Language | Python 3
| Runtime | 4065 ms, faster than 5.00% of Python3 online submissions for Kth Largest Element in an Array
| Memory Usage | 124.4 MB, less than 5.51% of Python3 online submissions for Kth Largest Element in an Array
| Datastructures | List[int]
| Algorithms | QuickSelect
| Complexity | Average Time: O(n), Space: O(n)

### Procedure

1. ...

### Code

```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        # Greater, equal, and less than the pivot point
        greater = [ n for n in nums if n >  nums[0] ]
        equal   = [ n for n in nums if n == nums[0] ]
        less    = [ n for n in nums if n <  nums[0] ]
        
        L, M = len(greater), len(equal)
        
        if k <= L:   return self.findKthLargest(greater,k)
        if k >  L+M: return self.findKthLargest(less,k-L-M)
        return equal[0]
```
