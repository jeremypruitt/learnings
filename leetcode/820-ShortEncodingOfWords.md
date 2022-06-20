# 820 - Short Encoding of Words

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/short-encoding-of-words/
| Language | Python 3
| Runtime | 52 ms, faster than 88.99% of Python3 online submissions for Short Encoding of Words
| Memory Usage | 14.5 MB, less than 91.74% of Python3 online submissions for Short Encoding of Words
| Datastructures | List[str]
| Algorithms | Group + Least Common Prefix?
| Complexity | Time: O(NlogN) Memory: O(NK^2) (K=max length of words, N=number of words)

### Procedure

1. ...

### Code

```python
class Solution:
    def minimumLengthEncoding(self, words: List[str]) -> int:
        word_set = set(words)
        for word in words:
            if word in word_set:
                for i in range(1,len(word)):
                    word_set.discard(word[i:])
        return len( "#".join( list(word_set) )) + 1
        # OR you can use this:
        #return sum(len(word) + 1 for word in word_set)

```
