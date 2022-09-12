# 948 - Bag of Tokens

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/bag-of-tokens/
| Language | Python 3
| Runtime | 103 ms, faster than 26.89% of Python3 online submissions for Bag of Tokens
| Memory Usage | 14 MB, less than 77.36% of Python3 online submissions for Bag of Tokens
| Datastructures | deque, List[int]
| Algorithms | Sort + Greedy
| Complexity | Time: O(NlogN) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def bagOfTokensScore(self, tokens: List[int], power: int) -> int:
        Q, score = deque(sorted(tokens)), 0
        
        while Q and power >= Q[0]:
            while Q and power >= Q[0]:
                power -= Q.popleft()
                score += 1
            if score > 0 and len(Q) > 1:
                power += Q.pop()
                score -= 1
        
        return score
```
