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

#### One-Liner

```python
class Solution:
    def numberOfSteps(self, num: int) -> int:
        return bin(num)[2:].count('1') * 2 + bin(num)[2:].count('0') - 1
```

#### Longer w/ Explanation
```python
class Solution:
    def numberOfSteps(self, num: int) -> int:
        return bin(num)[2:].count('1') * 2 + bin(num)[2:].count('0') - 1

        # Convert to binary, and remove the "0b" from the front
        binary_num = bin(num)[2:]

        # Get a count of 1s and 0s
        number_of_ones = binary_num.count('1')
        number_of_zeros = binary_num.count('0')
        
        # Each 1 divides by two, so we offest by multiplying by two
        subtotal_ones = number_of_ones * 2
        
        # Last step is to subtract 1
        subtotal_zeros = number_of_zeros - 1
        
        # Return the sum of both subtotals
        return subtotal_ones + subtotal_zeros
```
