# 792 - Number of Matching Subsequences

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/number-of-matching-subsequences/
| Language | Python 3
| Runtime | 360 ms, faster than 96.34% of Python3 online submissions for Number of Matching Subsequences
| Memory Usage | 15.6 MB, less than 51.10% of Python3 online submissions for Number of Matching Subsequences
| Datastructures | List[str]
| Algorithms | ?
| Complexity | Time: ? Memory: ?

### Procedure

1. ...

### Code

```python
class Solution:
    def numMatchingSubseq(self, s: str, words: List[str]) -> int:
        word_dict, result = defaultdict(list), 0
        
        for word in words: word_dict[word[0]].append(word)            
        
        for char in s:
            if char in word_dict:
                words_expecting_char = word_dict.pop(char)
                for word in words_expecting_char:
                    if len(word) == 1:
                        result += 1
                    else:
                        word_dict[word[1]].append(word[1:])
        return result
```
