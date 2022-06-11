# 1658 - Minimum Operations to Reduce X to Zero

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/
| Language | Python 3
| Runtime | 1199 ms, faster than 91.32% of Python3 online submissions for Minimum Operations to Reduce X to Zero
| Memory Usage | 27.9 MB, less than 82.16% of Python3 online submissions for Minimum Operations to Reduce X to Zero
| Datastructures | List[int]
| Algorithms | Two Pointers

### Procedure

1. TBD...

### Code

```python
class Solution:
    def minOperations(self, nums: List[int], x: int) -> int:
        sum_of_nums = sum(nums)
        if sum_of_nums < x:  return -1
        if sum_of_nums == x: return len(nums)
        
        required_subarray_sum = sum_of_nums - x
        left = current_sum = max_subarray_size = 0
        for right, num in enumerate(nums):
            current_sum += num
            while current_sum > required_subarray_sum:
                current_sum -= nums[left]
                left += 1
            if current_sum == required_subarray_sum:
                max_subarray_size = max(max_subarray_size, right-left+1)
        
        return len(nums) - max_subarray_size if max_subarray_size > 0 else -1
```
