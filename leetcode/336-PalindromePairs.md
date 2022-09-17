# 336 - Palindrome Pairs

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/palindrome-pairs/
| Language | Python 3
| Runtime | 3350 ms, faster than 80.91% of Python3 online submissions for Palindrome Pairs
| Memory Usage | 26.2 MB, less than 93.16% of Python3 online submissions for Palindrome Pairs
| Datastructures | Dict, List[str]
| Algorithms | Iteration (Divide & Conquer?)
| Complexity | Time: O(N*W^2?) Memory: O(?)

### Procedure

1. ...

### Code

```python
class Solution:
    def palindromePairs(self, words: List[str]) -> List[List[int]]:
        result = []
        d = {word[::-1]: i for i, word in enumerate(words)}
        
        for i, word in enumerate(words): 
            for j in range(len(word) + 1):
                prefix, suffix = word[:j], word[j:]
                
                if prefix in d and i != d[prefix] and suffix == suffix[::-1]: 
                    result.append([i, d[prefix]])
                
                if suffix in d and i != d[suffix] and prefix == prefix[::-1] and j>0: 
                    result.append([d[suffix], i])
        
        return result
```
