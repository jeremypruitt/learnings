# 704 - Binary Search

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/binary-search/
| Language | Python 3
| Runtime | 263 ms, faster than 82.93% of Python3 online submissions for Binary Search
| Memory Usage | 15.5 MB, less than 71.63% of Python3 online submissions for Binary Search
| Datastructures | List[int]
| Algorithms | Two Pointer

### Procedure

1. ...

### Code

#### Option 1: Verbose

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left_index, right_index = 0, len(nums) - 1
        while left_index <= right_index:
            middle_index = (left_index + right_index) // 2
            if nums[middle_index] < target:
                left_index = middle_index + 1
            elif nums[middle_index] > target:
                right_index = middle_index - 1
            else:
                return middle_index
        
        return -1
```

#### Option 2: Terse w/ Bisect

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        index = bisect.bisect_left(nums, target)
        if index < len(nums) and nums[index] == target:
            return index
        else:
            return -1
```
