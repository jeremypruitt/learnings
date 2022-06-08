# 1332 - Remove Palindromic Subsequences

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/remove-palindromic-subsequences/
| Language | Python 3
| Runtime | 35 ms, faster than 68.78% of Python3 online submissions for Remove Palindromic Subsequences
| Memory Usage | 13.8 MB, less than 53.87% of Python3 online submissions for Remove Palindromic Subsequences
| Datastructures | String
| Algorithms | Reverse string

### Procedure

1. TBD...

### Code

#### Option 1 

```python
class Solution:
    def removePalindromeSub(self, s: str) -> int:
        # Don't confuse subarry with subsequence.
        # Subarrays are consecutive.
        # Subsequence don't have to be consecutive.

        if not s: return 0        # Empty String
        if s == s[::-1]: return 1 # Palindrome
        return 2
```

#### Option 2: One-Liner

```python
class Solution:
    def removePalindromeSub(self, s: str) -> int:
        return 1 if s == s[::-1] else 2
```
