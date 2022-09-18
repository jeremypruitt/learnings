# 42 - Trapping Rain Water

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/trapping-rain-water/
| Language | Python 3
| Runtime | 113 ms, faster than 99.45% of Python3 online submissions for Trapping Rain Water
| Memory Usage | 16 MB, less than 81.24% of Python3 online submissions for Trapping Rain Water
| Datastructures | List[int]
| Algorithms | Two-Pointers
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        if not height: return 0
        
        left, right = 0, len(height) - 1
        max_left, max_right = height[left], height[right]
        max_trapped_water = 0
        
        while left <= right:
            if max_left < max_right: # max left water is trapped
                max_left = max(max_left, height[left])
                max_trapped_water += max_left - height[left]
                left += 1
            else: # max right water is trapped
                max_right = max(max_right, height[right])
                max_trapped_water += max_right - height[right]
                right -= 1

        return max_trapped_water
```
