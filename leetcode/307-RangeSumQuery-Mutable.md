# 307 - Range Sum Query - Mutable

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/range-sum-query-mutable/
| Language | Python 3
| Runtime | 8841 ms, faster than 5.00% of Python3 online submissions for Range Sum Query - Mutable
| Memory Usage | 31.2 MB, less than 66.27% of Python3 online submissions for Range Sum Query - Mutable
| Datastructures | List[int]
| Algorithms | Range Sum Query
| Complexity | Time: O(logN) Memory: O(1)

### Procedure

1. ...

### Code

```python
class NumArray:
    def __init__(self, nums: List[int]):
        self.nums = nums
        self.sums = sum(nums)

    def update(self, index: int, val: int) -> None:
        self.sums += val - self.nums[index]
        self.nums[index] = val

    def sumRange(self, left: int, right: int) -> int:
        if right-left < len(self.nums) // 2: return sum(self.nums[left:right+1])
        return self.sums - sum(self.nums[:left]) - sum(self.nums[right+1:])

# Your NumArray object will be instantiated and called as such:
# obj = NumArray(nums)
# obj.update(index,val)
# param_2 = obj.sumRange(left,right)
```
