# 318 - Maximum Product of Word Lengths

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/maximum-product-of-word-lengths/
| Language | Python 3
| Runtime | 428 ms, faster than 84.89% of Python3 online submissions for Maximum Product of Word Lengths
| Memory Usage | 14.2 MB, less than 93.57% of Python3 online submissions for Maximum Product of Word Lengths
| Datastructures | List[str], Dict[bitmask]
| Algorithms | bitmask, iterate, xor, lambda/reduce

### Procedure

1. TBD...

### Code

#### Option 1: Submitted Solution

```python
class Solution:
    def maxProduct(self, words: List[str]) -> int:
        max_val = 0
        cache = defaultdict(int)
        
        for word in words:
            for char in set(word):
                cache[word] |= 1<<(ord(char) - ord('a'))
        
        for word1, word2 in combinations(cache,2):
            if cache[word1] & cache[word2] == 0:
                max_val = max(max_val, len(word1) * len(word2))
        
        return max_val
```

#### Option 2: Alternative Solution

```python
class Solution:
    def maxProduct(self, words: List[str]) -> int:
        word_count = len(words)
        masks   = [0] * word_count
        lengths = [0] * word_count

        for i in range(word_count):
            for char in words[i]:
                masks[i] |= 1<<(ord(char) - ord('a'))
            lengths[i] = len(words[i])

        for i in range(word_count):
            for j in range(i+1, word_count):
                if not (masks[i] & masks[j]):
                    max_val = max(max_val, lengths[i] * lengths[j])

        return max_val
```
