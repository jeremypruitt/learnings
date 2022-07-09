# 1696 - Jump Game VI

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/jump-game-vi/
| Language | Python 3
| Runtime | 1552 ms, faster than 51.73% of Python3 online submissions for Jump Game VI
| Memory Usage | 28.1 MB, less than 47.64% of Python3 online submissions for Jump Game VI
| Datastructures | List[int], deque
| Algorithms | DP + Decreasing Deque
| Complexity | Time: O(N) Memory: O(K) (C=length of nums, K=max steps to jump)

### Procedure

1. ...

### Code

```python
class Solution:
    def maxResult(self, nums: List[int], k: int) -> int:
        dq = deque([0])
        for i in range(1, len(nums)):
            while dq and dq[0] < i - k: dq.popleft()
            nums[i] += nums[ dq[0] ]
            while dq and nums[i] >= nums[ dq[-1] ]: dq.pop()
            dq.append(i)
        
        return nums[-1]
```
