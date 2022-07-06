# 509 - Fibonacci Number

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/fibonacci-number/
| Language | Python 3
| Runtime | 24 ms, faster than 99.07% of Python3 online submissions for Fibonacci Number
| Memory Usage | 13.8 MB, less than 54.45% of Python3 online submissions for Fibonacci Number
| Datastructures | int
| Algorithms | DP
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. Loop n times
2. A becomes B, and B becomes A+B
3. When we get to end, A contains the answer

### Code

```python
class Solution:
    def fib(self, n: int) -> int:
        if n <= 1: return n
        a, b = 0, 1
        for _ in range(n): a, b = b, a+b
        return a
```
