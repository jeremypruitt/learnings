# 658 - Find K Closest Elements

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-k-closest-elements/submissions/
| Language | Python 3
| Runtime | 602 ms, faster than 39.84% of Python3 online submissions for Find K Closest Elements
| Memory Usage | 15.6 MB, less than 45.71% of Python3 online submissions for Find K Closest Elements
| Datastructures | List[int]
| Algorithms | Binary Search
| Complexity | Time: O(log(N-K) Memory: O(C)

### Procedure

1. ...

### Code

```python
class Solution:
    def findClosestElements(self, arr: List[int], k: int, x: int) -> List[int]:
        left, right = 0, len(arr) - k
        
        while left < right:
            mid = (left + right) // 2
            if x > (arr[mid] + arr[mid+k]) // 2:
                left = mid + 1
            else:
                right = mid
        
        return arr[left:left+k]
```
