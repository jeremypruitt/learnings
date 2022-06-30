# 462 - Minimum Moves to Equal Array Elements II

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii/
| Language | Python 3
| Runtime | 95 ms, faster than 70.68% of Python3 online submissions for Minimum Moves to Equal Array Elements II
| Memory Usage | 15.3 MB, less than 95.33% of Python3 online submissions for Minimum Moves to Equal Array Elements II
| Datastructures | List[int]
| Algorithms | Math/Median
| Complexity | Time: O(NlogN) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def minMoves2(self, nums: List[int]) -> int:
        nums.sort()
        result, median = 0, nums[ len(nums) // 2 ]
        for num in nums: result += abs(median - num)
        return result
```
