# 1048 - Longest String Chain

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/longest-string-chain/
| Language | Python 3
| Runtime | 154 ms, faster than 87.73% of Python3 online submissions for Longest String Chain
| Memory Usage | 14.3 MB, less than 71.64% of Python3 online submissions for Longest String Chain
| Datastructures | List[str]
| Algorithms | DP (bottom-up)
| Complexity | Time: O(NlogN + N*L*L) Memory: O(n)

### Procedure

1. ...

### Code

```python
class Solution:
    def longestStrChain(self, words: List[str]) -> int:
        dp = {}
        result = 1
        
        for word in sorted(words,key=len):
            dp[word] = 1
            
            for i in range( len(word) ):
                previous_word = word[:i] + word[i + 1:]    
                if previous_word in dp:
                    # You could use something like this:
                    #   dp[word] = dp[previous_word] + 1
                    # But that only passes because the test
                    # cases are weak. Use this one for a
                    # more robust and general solution:
                    dp[word] = max(dp[previous_word] + 1, dp[word])

            result = max(result, dp[word])
        
        return result
```
