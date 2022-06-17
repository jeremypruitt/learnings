# 5 - Longest Palindromic Substring

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/longest-palindromic-substring/
| Language | Python 3
| Runtime | 935 ms, faster than 80.41% of Python3 online submissions for Longest Palindromic Substring
| Memory Usage | 13.9 MB, less than 90.69% of Python3 online submissions for Longest Palindromic Substring
| Datastructures | List[str]
| Algorithms | DP (bottom-up)
| Complexity | Time: O(n^2) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        def getLongestPalindrome(s):
            longest_palindrome = ""
            for i in range(len(s)):        
                odd  = palindromeAt(s, i, i)
                even = palindromeAt(s, i, i+1)
                longest_palindrome = max(longest_palindrome, odd, even, key=len)
            return longest_palindrome
 
        def palindromeAt( s, left, right):    
            while left >= 0 and right < len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return s[left+1:right]

        return getLongestPalindrome(s)
```
