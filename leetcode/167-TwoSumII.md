# 167 - Two Sum II (Input Array Is Sorted)

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/
| Language | Python 3
| Runtime | 176 ms, faster than 50.98% of Python3 online submissions for Two Sum II - Input Array Is Sorted
| Memory Usage | 14.8 MB, less than 89.05% of Python3 online submissions for Two Sum II - Input Array Is Sorted
| Datastructures | List[int]
| Algorithms | Two Pointers

### Procedure

1. Left pointer starts at first index
   Right pointer starts ar last index
2. Until the two pointers meet in the middle...
3. If sum of left and right matches the target we're done
4. If sum of left and right is less, increase left pointer
5. If sum of left and right is more, decrease right pointer

### Code

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        left, right = 0, len(numbers) - 1
        
        while left < right:
            if numbers[left] + numbers[right] == target:
                return [left+1, right+1]
            elif numbers[left] + numbers[right] < target:
                left += 1
            else:
                right -= 1
```
