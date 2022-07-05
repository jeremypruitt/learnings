# 128 - Longest Consecutive Sequence

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/longest-consecutive-sequence/
| Language | Python 3
| Runtime | 392 ms, faster than 81.47% of Python3 online submissions for Longest Consecutive Sequence
| Memory Usage | 28.6 MB, less than 42.76% of Python3 online submissions for Longest Consecutive Sequence
| Datastructures | Set(), List[int]
| Algorithms | Use set to build sequence
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        nums, sequence_length = set(nums), 0
        
        while nums:
            first = last = nums.pop()
            while first - 1 in nums: first -= 1; nums.remove(first)
            while last  + 1 in nums: last  += 1; nums.remove(last)
            sequence_length = max(sequence_length,last-first+1)
        
        return sequence_length
```
