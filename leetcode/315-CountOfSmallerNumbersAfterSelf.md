# 315 - Count of Smaller Numbers After Self

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/count-of-smaller-numbers-after-self/
| Language | Python 3
| Runtime | 2466 ms, faster than 92.95% of Python3 online submissions for Count of Smaller Numbers After Self
| Memory Usage | 35.1 MB, less than 49.01% of Python3 online submissions for Count of Smaller Numbers After Self
| Datastructures | List[int]
| Algorithms | Binary Search
| Complexity | Time: O(NlogN) Memory: O(N)

### Procedure

1. ...

### Code

#### Option 1: Use SortedList

```python
from sortedcontainers import SortedList

class Solution:
    def countSmaller(self, nums: List[int]) -> List[int]:
        result,  sortedList = deque(),  SortedList()
        for num in nums[::-1]:
            result.appendleft(sortedList.bisect_left(num))
            sortedList.add(num)
        return result
```

#### Option 2

```python
class Solution:
    def countSmaller(self, nums: List[int]) -> List[int]:
        for num in nums:
            i = bisect_left(sorted_nums,num)
            result.append(i)
            del sorted_nums[i]
        return result
```
