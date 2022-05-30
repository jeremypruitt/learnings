# 29 - Divide Two Integers

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/divide-two-integers/
| Language | Python 3
| Runtime | 41 ms, faster than 66.22% of Python3 online submissions for Divide Two Integers
| Memory Usage | 13.8 MB, less than 76.13% of Python3 online submissions for Divide Two Integers
| Datastructures | List[str], Dict[bitmask]
| Algorithms | int

### Procedure

1. TBD...

### Code

```python
class Solution:
    def divide(self, dividend: int, divisor: int) -> int:
        is_negative = (dividend < 0) != (divisor < 0)
        divisor, dividend = abs(divisor), abs(dividend)
        
        quotient = 0
        total = divisor
        
        while total <= dividend:
            current_quotient = 1
            while (total << 1) <= dividend:
                total <<= 1
                current_quotient <<= 1

            # Example without bitwise operator:
            #while (total + total) <= dividend:
            #    total += total
            #    current_quotient += current_quotient
            
            dividend -= total
            total = divisor
            quotient += current_quotient
        
        quotient = -quotient if is_negative else quotient
        quotient = max(quotient, -2147483648)
        return min(2147483647, quotient)
```
