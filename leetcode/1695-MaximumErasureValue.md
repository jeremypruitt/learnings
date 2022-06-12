# 1695 - Maximum Erasure Value

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/maximum-erasure-value/
| Language | Python 3
| Runtime | 1972 ms, faster than 41.38% of Python3 online submissions for Maximum Erasure Value
| Memory Usage | 27.6 MB, less than 49.23% of Python3 online submissions for Maximum Erasure Value
| Datastructures | List[int], Set
| Algorithms | Sliding Window / Two Pointers

### Procedure

1. Create sliding window
2. For each num in list, check if already present in window/cache
3. If num in window, shrink window from left
4. Add num to max score and repeat

### Code

```python
class Solution:
    def maximumUniqueSubarray(self, nums: List[int]) -> int:
        cache = set()
        current_score, maximum_score, left = 0, 0, 0
        for num in nums:
            while num in cache:
                current_score -= nums[left]
                cache.remove(nums[left])
                left += 1
            current_score += num
            cache.add(num)
            maximum_score = max(maximum_score, current_score)
        return maximum_score
```
