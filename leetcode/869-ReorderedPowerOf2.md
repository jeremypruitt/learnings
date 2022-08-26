# 869 - Reordered Power of 2

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/reordered-power-of-2/
| Language | Python 3
| Runtime | 55 ms, faster than 62.57% of Python3 online submissions for Reordered Power of 2
| Memory Usage | 13.9 MB, less than 26.74% of Python3 online submissions for Reordered Power of 2
| Datastructures | List[str]
| Algorithms | Counter & Bitshift
| Complexity | Time: O(log2N) Memory: O(logN)

### Procedure

1. Loop over every possible power of 2 (to 32)
2. Get power of 2 using bitwise op
3. Return success if we find a power of 2 with came counter profile as the provided int

### Code

```python
class Solution:
    def reorderedPowerOf2(self, n: int) -> bool:
        n_counter = Counter(str(n))
        
        # check each possible power of 2
        for i in range(32):
            # Get power of 2 w/ bitwise operation
            power_of_2 = 1 << i
                
            # Success if we find a power of 2 w/ same counter as n
            if Counter( str(power_of_2) ) == n_counter: return True
        
        return False
```
