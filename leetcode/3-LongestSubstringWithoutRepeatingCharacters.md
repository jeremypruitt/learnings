# 3 - Longest Substring Without Repeating Characters

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/longest-substring-without-repeating-characters/
| Language | Python 3
| Runtime | 53 ms, faster than 97.82% of Python3 online submissions for Longest Substring Without Repeating Characters
| Memory Usage | 14 MB, less than 48.71% of Python3 online submissions for Longest Substring Without Repeating Characters
| Datastructures | List[List[int]]
| Algorithms | Sliding Window
| Complexity | Time: O(n) Memory: O(m)

### Procedure

1. ...

### Code

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        cache = {}
        left = longest_substring = 0
        for right in range(len(s)):
            # If s[right] not in seen, we can keep increasing
            # the window size by moving right pointer
            if s[right] not in cache:
                longest_substring = max(longest_substring,right - left +1)
            else:
                # case2: s[right] is not inside the current window,
                # so we can keep increase the window
                if cache[ s[right] ] < left:
                    longest_substring = max(longest_substring, right - left + 1)
                
                # case2: s[right] is inside the current window,
                # so we need to change the window by moving
                # left pointer to cache[ s[right] ] + 1.
                else:
                    left = cache[ s[right] ] + 1
            
            cache[ s[right] ] = right
        
        return longest_substring
```
