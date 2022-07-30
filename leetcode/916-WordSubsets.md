# 916 - Word Subsets

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/word-subsets/
| Language | Python 3
| Runtime | 829 ms, faster than 86.33% of Python3 online submissions for Word Subsets
| Memory Usage | 19 MB, less than 15.00% of Python3 online submissions for Word Subsets
| Datastructures | List[str]
| Algorithms | Brute Force?
| Complexity | Time: O(M+N)? Memory: O(M+N)? (M=length of words1, N=length of words2)

### Procedure

1. ...

### Code

```python
class Solution:
    def wordSubsets(self, words1: List[str], words2: List[str]) -> List[str]:
        universal_strings = set(words1)
        required_letters = {}
        for word2 in words2:
            for char in word2:
                count = word2.count(char)
                if char not in required_letters or count > required_letters[char]:
                    required_letters[char] = count

        for word1 in words1:
            for letter in required_letters:
                if word1.count(letter) < required_letters[letter]:
                    universal_strings.remove(word1)
                    break
        
        return list(universal_strings)
```
