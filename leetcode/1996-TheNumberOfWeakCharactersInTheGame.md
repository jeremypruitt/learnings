# 1996 - The Number of Weak Characters in the Game

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/the-number-of-weak-characters-in-the-game/
| Language | Python 3
| Runtime | 4969 ms, faster than 6.75% of Python3 online submissions for The Number of Weak Characters in the Game
| Memory Usage | 67 MB, less than 79.12% of Python3 online submissions for The Number of Weak Characters in the Game
| Datastructures | List[List[int]]
| Algorithms | Sort + Greedy
| Complexity | Time: O(NlogN) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def numberOfWeakCharacters(self, properties: List[List[int]]) -> int:
        number_of_weak_characters = max_defense = 0
        
        properties.sort(key = lambda x : (-x[0],x[1]))        
        
        for attack, defense in properties:
            if defense < max_defense: number_of_weak_characters += 1
            max_defense = max(max_defense, defense)
        
        return number_of_weak_characters
```
