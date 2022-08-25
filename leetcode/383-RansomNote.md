# 383 - Ransom Note

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/ransom-note/
| Language | Python 3
| Runtime | 75 ms, faster than 71.03% of Python3 online submissions for Ransom Note
| Memory Usage | 14.2 MB, less than 53.79% of Python3 online submissions for Ransom Note
| Datastructures | str, dict
| Algorithms | Counter Compare
| Complexity | Time: O(M+N) Memory: O(N) (M=length of ransom note, N=length of magazine)

### Procedure

1. ...

### Code

#### Option 1

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        return not Counter(ransomNote) - Counter(magazine)
```

#### Option 2

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        return (Counter(ransomNote) - Counter(magazine)) == {}
```

#### Option 3

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        magazine_count = Counter(magazine)
        for letter, count in Counter(ransomNote).items():
            if magazine_count[letter] <= count:
                return False
        
        return True
```
