# 97 - Interleaving String

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/interleaving-string/
| Language | Python 3
| Runtime | 78 ms, faster than 31.90% of Python3 online submissions for Interleaving String
| Memory Usage | 13.8 MB, less than 98.69% of Python3 online submissions for Interleaving String
| Datastructures | str, DP Array
| Algorithms | DP
| Complexity | Time: O(NM) Memory: O(M) (N=number of chars in s1, M=number of chars in s2)

### Procedure

1. Grab length of s1 & s2, and fail early if their sum is greater than s3
2. Pre-populate a DP array
3. Loop through s2...
   1. Mark dp false if i doesn't have a previous element or doesn't exist in s3
4. Loop through s1...
   1. Mark first element false if s1 value doesn't exist in s3 or if first element is already marked false in dp
   2. For each value of s1, loop through s2...
      1. Mark s2 value +1 true if exists in dp and exists in s1 or s2 at i+j+1 in s3
5. If last value is still true then success

### Code

```python
class Solution:
    def isInterleave(self, s1: str, s2: str, s3: str) -> bool:
        # Grab length of s1 & s2, and fail early if their
        # sum is greater than s3
        n, m = len(s1), len(s2)
        if n+m != len(s3): return False
        
        # Pre-populate a DP array
        dp = [True] * (m + 1)
        
        # Loop through s2...
        for i in range(1,m+1):
            # Mark dp false if i doesn't have a previous
            # element or doesn't exist in s3
            dp[i] = dp[i-1] and s2[i-1] == s3[i-1]
        
        # Loop through s1...
        for i in range(n):
            # Mark first element false if s1 value doesn't
            # exist in s3 or if first element is already
            # marked false in dp
            dp[0] = dp[0] and s1[i] == s3[i]
            
            # For each value of s1, loop through s2...
            for j in range(m):
                # Mark s2 value +1 true if exists in dp
                # and exists in s1 or s2 at i+j+1 in s3
                dp[j+1] = (
                    # 
                    (dp[j+1] and s1[i] == s3[i+j+1]) or
                    (dp[j]   and s2[j] == s3[i+j+1]) )
        
        # If last value is still true then success
        return dp[-1]
```
