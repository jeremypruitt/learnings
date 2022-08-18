# 1338 - Reduce Array Size to The Half

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/reduce-array-size-to-the-half/
| Language | Python 3
| Runtime | 994 ms, faster than 45.87% of Python3 online submissions for Reduce Array Size to The Half
| Memory Usage | 35.7 MB, less than 44.35% of Python3 online submissions for Reduce Array Size to The Half
| Datastructures | List[int]
| Algorithms | Most Common + Iteration
| Complexity | Time: O(NlogN) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def minSetSize(self, arr: List[int]) -> int:
        count = 0
        most_common_integers = Counter(arr).most_common()
        
        for i in range(len(most_common_integers)):
            count += most_common_integers[i][1]
            if count >= len(arr) // 2: return i + 1
```
