# 936 - Stamping The Sequence

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/stamping-the-sequence/
| Language | Python 3
| Runtime | 142 ms, faster than 85.07% of Python3 online submissions for Stamping The Sequence
| Memory Usage | 20.8 MB, less than 5.97% of Python3 online submissions for Stamping The Sequence
| Datastructures | List[int], Memo
| Algorithms | DP (Top-Down DFS + Memoization)
| Complexity | Time: O(ClogC) Memory: O(C) (C=number of characters in all words in array)

### Procedure

1. ...

### Code

```python
class Solution:
    def movesToStamp(self, stamp: str, target: str) -> List[int]:
        memo, stamp_length = {}, len(stamp)
        
        def dfs(s, t, seqs):
            if t == len(target):
                memo[s, t] = seqs if s == stamp_length else []
            
            if (s, t) not in memo:
                if s == stamp_length:
                    for i in range(stamp_length):
                        cand = dfs(i, t, [t-i]+seqs)
                        if cand:
                            memo[s, t] = cand
                            break
                    else: 
                        memo[s, t] = []
                elif target[t] == stamp[s]:
                    cand = dfs(s+1, t+1, seqs)
                    memo[s, t] = cand if cand else dfs(0, t+1, seqs+[t+1])
                else:
                    memo[s, t] = []
            return memo[s, t]
        
        return dfs(0, 0, [0])
```
