# 665 - Non-decreasing Array

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/non-decreasing-array/
| Language | Python 3
| Runtime | 217 ms, faster than 76.12% of Python3 online submissions for Non-decreasing Array
| Memory Usage | 15.4 MB, less than 15.99% of Python3 online submissions for Non-decreasing Array
| Datastructures | List[int]
| Algorithms | Greedy?
| Complexity | Time: O(n) Memory: O(1)

### Procedure

1. ...

### Code

Option 1: Working Code

```python
class Solution:
    def checkPossibility(self, nums: List[int]) -> bool:
        a, b = nums[:], nums[:]
        for i in range( len(nums) - 1):
            if nums[i] > nums[i+1]:
                a[i] = nums[i+1]
                b[i+1] = nums[i]
                break
        
        return a == sorted(a) or b == sorted(b)
```

#### Option 2: Not Working, but More Readable

This code doesn't work with all test cases, and I didn't figure out the edge cases. Keeping here for posterity or potential future motivation to complete.

```python
class Solution:
    def checkPossibility(self, nums: List[int]) -> bool:
        flag, nums_length = False, len(nums)            
        
        def numsIsModifiable():
            (
                i + 2 < nums_length and nums[i + 2] < nums[i]
            ) and (
                i > 0 and nums[i + 1] < nums[i - 1]
            )

        for i in range(nums_length - 1):
            if nums[i+1] < nums[i]:
                if flag: return False
                if numsIsModifiable(): return False
                flag = True

        return True
```
