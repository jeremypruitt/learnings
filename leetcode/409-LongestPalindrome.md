# 409 - Longest Palindrome

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/longest-palindrome/
| Language | Python 3
| Runtime | 71 ms, faster than 8.40% of Python3 online submissions for Longest Palindrome
| Memory Usage | 13.8 MB, less than 97.58% of Python3 online submissions for Longest Palindrome
| Datastructures | Seen-Hash
| Algorithms | Iterate + Seen-Hash
| Complexity | Time: O(n) Memory: O(1)

### Procedure

1. ...

### Code

```python
hash = set()
        for c in s:
            if c not in hash:
                hash.add(c)
            else:
                hash.remove(c)
        # len(hash) is the number of the odd letters
        return len(s) - len(hash) + 1 if len(hash) > 0 else len(s)
```
