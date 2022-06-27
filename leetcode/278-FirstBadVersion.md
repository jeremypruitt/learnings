# 278 - First Bad Version

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/first-bad-version/
| Language | Python 3
| Runtime | 44 ms, faster than 51.43% of Python3 online submissions for First Bad Version
| Memory Usage | 13.9 MB, less than 60.55% of Python3 online submissions for First Bad Version
| Datastructures | int
| Algorithms | Binary Search (with two pointers)
| Complexity | Time: O(NlogN), Space: O(1)

### Procedure

1. ...

### Code

```python
# The isBadVersion API is already defined for you.
# def isBadVersion(version: int) -> bool:
class Solution:
    def firstBadVersion(self, n: int) -> int:
        left, right = 1, n
        while left < right:
            middle = left + (right-left) // 2
            if isBadVersion(middle): right = middle
            else: left = middle + 1
        return left
```
