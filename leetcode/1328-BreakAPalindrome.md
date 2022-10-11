# 1328 - Break a Palindrome

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/break-a-palindrome/submissions/
| Language | Python 3
| Runtime | 43 ms, faster than 72.42% of Python3 online submissions for Break a Palindrome
| Memory Usage | 13.8 MB, less than 61.30% of Python3 online submissions for Break a Palindrome
| Datastructures | str
| Algorithms | Greedy?
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def breakPalindrome(self, palindrome: str) -> str:
        length_of_palindrome = len(palindrome)
        if length_of_palindrome == 1:  return ""
        half_length_of_palindrome = length_of_palindrome // 2
        
        for i in range(half_length_of_palindrome):
            if palindrome[i] != 'a':
                return palindrome[:i] + 'a' + palindrome[i+1:]
        
        return palindrome[:-1] + 'b'
```
