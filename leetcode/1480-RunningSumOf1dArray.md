# 1480 - Running Sum of 1d Array

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/running-sum-of-1d-array/
| Language | Python 3
| Runtime | 50 ms, faster than 65.50% of Python3 online submissions for Running Sum of 1d Array
| Memory Usage | 13.9 MB, less than 94.41% of Python3 online submissions for Running Sum of 1d Array
| Datastructures | List[int]
| Algorithms | iterate, sum, accumulate

### Procedure

1. TBD...

### Code

#### Option 1: Iterate a Running Total in New List

```python
    def runningSum(self, nums: List[int]) -> List[int]:
        answer = []
        running_total = 0
        
        for num in nums:
            running_total += num
            answer.append(running_total)
        
        return answer
```

#### Option 2: Iterate a Running Total in Place

```python
    def runningSum(self, nums: List[int]) -> List[int]:
        for i in range(1,len(nums)):
            nums[i] += nums[i-1]
        return nums
```

#### Option 3: One-Liner w/ Enumerate

```python
    def runningSum(self, nums: List[int]) -> List[int]:
        return [ sum(nums[:i]) for i, _ in enumerate(nums,1) ]
```

#### Option 4: One-Liner w/ Range/Len

```python
    def runningSum(self, nums: List[int]) -> List[int]:
        return [ sum(nums[:i+1]) for i in range(len(nums)) ]
```

#### Option 5: One-Liner w/ Built-In Accumulate Function

```python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        return accumulate(nums)
```
