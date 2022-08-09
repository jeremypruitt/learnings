# 473 - Matchsticks to Square

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/matchsticks-to-square/
| Language | Python 3
| Runtime | 670 ms, faster than 71.58% of Python3 online submissions for Matchsticks to Square
| Memory Usage | 14 MB, less than 61.50% of Python3 online submissions for Matchsticks to Square
| Datastructures | List[int]
| Algorithms | DFS
| Complexity | Time: O(4^N?) Memory: O(N) (C=number of characters in all words in array)

### Procedure

1. ...

### Code

```python
class Solution:
    def makesquare(self, matchsticks: List[int]) -> bool:
        perimeter = sum(matchsticks)
        side_length = perimeter / 4
        sides = [0] * 4
        longest_matchstick = max(matchsticks)
        number_of_matchsticks = len(matchsticks)
        
        def perimeter_divisible_by_four(n): return perimeter % 4 == 0
        
        def matchsticks_small_enough(n): return longest_matchstick <= side_length
        
        def have_enough_matchsticks(n): return number_of_matchsticks >= 4
        
        def problem_is_valid(nums):
            return (
                have_enough_matchsticks(nums) and
                matchsticks_small_enough(nums) and
                perimeter_divisible_by_four(nums) )

        if not problem_is_valid(matchsticks): return False
        matchsticks.sort(reverse=True)

        def dfs(cur):
            if cur == len(matchsticks):
                return sides[0] == sides[1] == sides[2] == side_length
            for i in range(4):
                if sides[i] + matchsticks[cur] <= side_length:
                    sides[i] += matchsticks[cur]
                    if dfs(cur+1): return True
                    sides[i] -= matchsticks[cur]
                    if sides[i] == 0: break
            return False
        
        return dfs(0)
```
