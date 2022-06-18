# 745 - Prefix and Suffix Search

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/prefix-and-suffix-search/
| Language | Python 3
| Runtime | 2251 ms, faster than 37.01% of Python3 online submissions for Prefix and Suffix Search
| Memory Usage | 38 MB, less than 53.82% of Python3 online submissions for Prefix and Suffix Search
| Datastructures | WordFilter
| Algorithms | Bruteforce
| Complexity | Time: O(nL^3 + QL) Memory: O(nL^3) (n=words, L=length of word, Q=number of queries)

### Procedure

1. ...

### Code

#### Option 1: Two For Loops

```python
class WordFilter:
    def __init__(self, words: List[str]):
        self.cache = {}
        for weight, word in enumerate(words):
            for i, j in product( range( len(word)+1 ), repeat=2):
                self.cache[word[:i]+"."+word[j:]] = weight

    def f(self, prefix: str, suffix: str) -> int:
        return self.cache.get(prefix+"."+suffix, -1)
```

#### Option 3: Three For Loops

```python
class WordFilter:
    def __init__(self, words: List[str]):
        self.cache = {}
        for weight, word in enumerate(words):
            for i in range( len(word) + 1 ):
                for j in range( len(word) + 1):
                    self.cache[word[:i]+"."+word[j:]] = weight

    def f(self, prefix: str, suffix: str) -> int:
        return self.cache.get(prefix+"."+suffix, -1)
```

#### Option 3: One-Liner

```python
class WordFilter:
    def __init__(self, words: List[str]):
        W = ' '.join(w + '=' + w for w in words[::-1])
        self.f = lambda p, s: W.count('=', W.find(s + '=' + p)) - 1
```

#### Option 4: Expanded One-Liner

```python
class WordFilter:
    def __init__(self, words):        
        self.cache = []
        for word in reversed(words):
            self.cache.append(word+'.'+word) 
        self.cache = ' '.join(self.cache)
    
    def f(self, prefix, suffix):
        return self.cache.count('.', self.cache.find( suffix+'.'+prefix ))-1
```
