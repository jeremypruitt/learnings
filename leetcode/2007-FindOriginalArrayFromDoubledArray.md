# 2007 - Find Original Array From Doubled Array

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/find-original-array-from-doubled-array/
| Language | Python 3
| Runtime | 2406 ms, faster than 42.32% of Python3 online submissions for Find Original Array From Doubled Array
| Memory Usage | 32.8 MB, less than 33.24% of Python3 online submissions for Find Original Array From Doubled Array
| Datastructures | Counter
| Algorithms | Greedy + Counter
| Complexity | Time: O(KlogK) Memory: O( N) (K=number of distinct keys in Counter hash)

### Procedure

1. ...

### Code

```python
class Solution:
    def findOriginalArray(self, changed: List[int]) -> List[int]:
        count_of = collections.Counter(changed)
        
        # If we have zeros, ensure we have even number of them
        if count_of[0] % 2: return []
        
        for num in sorted(count_of):
            if count_of[num] > count_of[2*num]: return []
            if num: count_of[2*num] -= count_of[num] 
            else:   count_of[2*num]  = count_of[num] // 2
        
        return list(count_of.elements())
```
