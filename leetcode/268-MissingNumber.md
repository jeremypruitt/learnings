# 268 - Missing Number

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/missing-number/
| Language | Python 3
| Runtime | 148 ms, faster than 77.91% of Python3 online submissions for Missing Number
| Memory Usage | 15.5 MB, less than 14.37% of Python3 online submissions for Missing Number
| Datastructures | List[int]
| Algorithms | iterate, xor, lambda/reduce

### Procedure

1. TBD...

### Code

#### Option 1: Iterate & XOR

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        answer = 0
        for i, num in enumerate(nums):
            answer ^= i + 1
            answer ^= num
        return answer
```

#### Option 2: Lambda & Reduce
```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        lambda_xor = lambda x,y: x ^ y
        nums_range = list(range(len(nums)+1))      
        return reduce(lambda_xor, nums_range + nums)
```

#### Option 3: One-liner Lambda & Reduce
```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        return reduce(lambda x,y: x ^ y, list(range(len(nums)+1)) + nums)
```
