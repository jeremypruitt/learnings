# 484 - Find Permutation

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-permutation/
| Language | Python 3
| Runtime | 116 ms, faster than 52.25% of Python3 online submissions for Find Permutation
| Memory Usage | 15.4 MB, less than 22.10% of Python3 online submissions for Find Permutation

```python
class Solution:
    def findPermutation(self, s: str) -> List[int]:
        result, stack = [], []
        
        for i in range(len(s)):
            stack.append(i+1)
            if s[i] == "I":
                while stack: result.append(stack.pop())
        
        stack.append(len(s)+1)
        while stack: result.append(stack.pop())
        
        return result
```
