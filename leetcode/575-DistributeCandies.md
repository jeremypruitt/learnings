# 575 - Distribute Candies

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/distribute-candies/
| Language | Python 3
| Runtime | 829 ms, faster than 91.21% of Python3 online submissions for Distribute Candies
| Memory Usage | 16.2 MB, less than 69.49% of Python3 online submissions for Distribute Candies
| Datastructures | List[int]
| Algorithms | Reverse string

### Procedure

1. TBD...

### Code

```python
class Solution:
    def distributeCandies(self, candies: List[int]) -> int:
        candies_to_eat = len(candies) / 2
        candy_types = len( set(candies) )
        return int( min(candies_to_eat, candy_types) )
```
