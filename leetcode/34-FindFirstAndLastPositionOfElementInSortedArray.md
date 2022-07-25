# 34 - Find First and Last Position of Element in Sorted Array

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/
| Language | Python 3
| Runtime | 95 ms, faster than 84.89% of Python3 online submissions for Find First and Last Position of Element in Sorted Array
| Memory Usage | 15.4 MB, less than 93.21% of Python3 online submissions for Find First and Last Position of Element in Sorted Array
| Datastructures | List[int]
| Algorithms | Binary Search
| Complexity | Time: O(logN) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        def binary_search(t):
            lo, hi = 0, len(nums)           
            while lo < hi:
                mid = (lo + hi) // 2
                if nums[mid] < t: lo = mid + 1
                else:             hi = mid                    
            return lo
        
        lo = binary_search(target)
        hi = binary_search(target + 1) - 1
        
        if lo <= hi: return [lo, hi]
        return [-1, -1]
```

#### Option 2

```python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        def binary_search(target,left,right):
            if left > right: return left
            middle = (left+right) // 2
            if target > nums[middle]: left = middle + 1
            else:                     right = middle - 1
            return binary_search(target,left,right)
        lower = binary_search(target - 0.5, 0, len(nums) - 1)
        upper = binary_search(target + 0.5, 0, len(nums) - 1)
        return [-1,-1] if lower == upper else [lower, upper-1]
```
