# 1342 - Number of Steps to Reduce a Number to Zero

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/
| Language | Python 3
| Runtime | 71 ms, faster than 5.24% of Python3 online submissions for Number of Steps to Reduce a Number to Zero
| Memory Usage | 13.8 MB, less than 53.50% of Python3 online submissions for Number of Steps to Reduce a Number to Zero
| Datastructures | int, bin
| Algorithms | int2bin

### Procedure

1. TBD...

### Code

```python
class Solution:
    def numberOfSteps(self, num: int) -> int:
        number_of_ones = bin(num).count('1') * 2
        number_of_zeros = bin(num).count('0') - 2
        return number_of_ones + number_of_zeros
```
