# 300 - Longest Increasing Subsequence

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/longest-increasing-subsequence/
| Language | Python 3
| Runtime | 96 ms, faster than 92.20% of Python3 online submissions for Longest Increasing Subsequence
| Memory Usage | 14.2 MB, less than 83.70% of Python3 online submissions for Longest Increasing Subsequence
| Datastructures | List[int]
| Algorithms | DP + Binary Search
| Complexity | Time: O(NlogN) Space: O(N)

### Procedure

1. ...

### Code

#### Option 1: DP + Binary Search

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        tails = [0] * len(nums)
        longest_strictly_increasing_subsequence = 0
        for num in nums:
            left, right = 0, longest_strictly_increasing_subsequence
            while left != right:
                middle = left + (right-left) // 2
                if tails[middle] < num:
                    left = middle+1
                else:
                    right = middle
            tails[left] = num
            longest_strictly_increasing_subsequence = max(longest_strictly_increasing_subsequence, left+1)
        return longest_strictly_increasing_subsequence
```

#### Option 2: DP - Time: O(N^2), Space: O(N)

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        if not nums: return 0
        N, dp = len(nums), [1] * N
        for i in range(N):
            for j in range(i):
                if nums[i] > nums[j]:
                    dp[i] = max(dp[i], dp[j]+1)
        return max(dp)
```

#### Option 3: Use Large Index

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp = [10**10] * (len(nums)+1)
        for num in nums: dp[bisect_left(dp,num)] = num
        return bisect_left(dp,10**10) # OR: return dp.index(10**10)
```

#### Option 4: Simple & Easy to Understand

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp = []
        for num in nums:
            i = bisect_left(dp, num)
            if i == len(dp): dp.append(num)
            else:            dp[i] = num
        return len(dp)
```
