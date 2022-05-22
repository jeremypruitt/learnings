# 647 - Palindromic Substrings

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/palindromic-substrings/
| Language | Python 3
| Runtime | 260 ms, faster than 36.58% of Python3 online submissions for Palindromic Substrings
| Memory Usage | 13.9 MB, less than 75.82% of Python3 online submissions for Palindromic Substrings
| Datastructures | string, int
| Algorithms | DP

### Procedure

1. TBD...

### Code

```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        result = 0
        
        for index in range(len(s)):
            result += self.findPalindromes(s, index, index)
            result += self.findPalindromes(s, index, index+1)
            
        return result
    
    def findPalindromes(self,s, left, right):
        result = 0
        while self.isInBounds(s,left,right) and self.isPalindrome(s,left,right):
            result += 1
            left   -= 1
            right  += 1
        return result
                    
    def isInBounds(self, s, left, right):
        return left >= 0 and right < len(s)
    
    def isPalindrome(self, s, left, right):
        return s[left] == s[right]

```
