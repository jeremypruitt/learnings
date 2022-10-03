# 1578 - Minimum Time to Make Rope Colorful

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/minimum-time-to-make-rope-colorful/
| Language | Python 3
| Runtime | 2878 ms, faster than 18.79% of Python3 online submissions for Minimum Time to Make Rope Colorful
| Memory Usage | 25 MB, less than 52.92% of Python3 online submissions for Minimum Time to Make Rope Colorful
| Datastructures | List[int]
| Algorithms | Greedy + Two-Pointers
| Complexity | Time: O(N) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def minCost(self, colors: str, neededTime: List[int]) -> int:
        left = result = 0
        for right in range(1, len(colors)):
            if colors[left] == colors[right]:
                if neededTime[left] < neededTime[right]:
                    result += neededTime[left]
                else:
                    result += neededTime[right]
                    continue 

            left = right
        
        return result
```
