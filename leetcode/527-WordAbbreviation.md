# 527 - Word Abbreviation

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/word-abbreviation/
| Language | Python 3
| Runtime | 787 ms, faster than 27.16% of Python3 online submissions for Word Abbreviation
| Memory Usage | 65.2 MB, less than 14.57% of Python3 online submissions for Word Abbreviation
| Datastructures | List[str]
| Algorithms | Group + Least Common Prefix?
| Complexity | Time: O(ClogC) Memory: O(C) (C=number of characters in all words in array)

### Procedure

1. ...

### Code

```python
class Solution:
    def wordsAbbreviation(self, words: List[str]) -> List[str]:
        groups = collections.defaultdict(int)
        
        for i, word in enumerate(words):
            for j in range(1, len(word) - 2):
                groups[ word[:j] + str( len(word)-j-1 ) + word[-1] ] += 1
        
        for i, word in enumerate(words):
            for j in range(1, len(word) - 2):
                new_group = word[:j] + str(len(word)-j-1) + word[-1]
                if groups[new_group] == 1:
                    words[i] = new_group
                    break
        
        return words
```
