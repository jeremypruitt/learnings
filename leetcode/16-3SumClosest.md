# 16 - 3Sum Closest

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/3sum-closest/submissions/
| Language | Python 3
| Runtime | 2513 ms, faster than 86.26% of Python3 online submissions for 3Sum Closest
| Memory Usage | 14.2 MB, less than 55.35% of Python3 online submissions for 3Sum Closest
| Datastructures | List[int]
| Algorithms | Sort + Two-Pointers
| Complexity | Time: O(N^2) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        nums.sort()
        
        total = sum(nums[:3])
        if total > target: return total

        total = sum(nums[-3:])
        if total < target: return total

        result = sum(nums[:3])
        for i in range(len(nums)):
            left, right = i+1, len(nums)-1
            
            while left < right:
                total = sum((nums[i], nums[left], nums[right]))
                
                if abs(total-target) < abs(result-target): result = total
                
                if   total < target:  left += 1
                elif total > target:  right -= 1
                else: return result
        
        return result
```
