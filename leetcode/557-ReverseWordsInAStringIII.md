# 557 - Reverse Words in a String III

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/reverse-words-in-a-string-iii/
| Language | Python 3
| Runtime | 83 ms, faster than 36.40% of Python3 online submissions for Reverse Words in a String III
| Memory Usage | 14.5 MB, less than 82.00% of Python3 online submissions for Reverse Words in a String III
| Datastructures | str
| Algorithms | Two-Pointers
| Complexity | Time: O(N) Memory: O(N) (C=number of characters in all words in array)

### Procedure

1. ...

### Code

#### Option 1: Two-Pointers

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        left = right = 0
        result = ''
        
        while right < len(s):
            if s[right] != ' ':
                right += 1
            else:
                result += s[left:right+1][::-1]
                left = right = right + 1
            
        result += ' ' + s[left:right][::-1]
        return result[1:]       
```

#### Option 2: One-Liner

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return " ".join(word[::-1] for word in s.split())            
```
