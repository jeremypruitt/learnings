# 1151 - Minimum Swaps to Group All 1's Together

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/minimum-swaps-to-group-all-1s-together/
| Language | Python 3
| Runtime | 837 ms, faster than 85.90% of Python3 online submissions for Minimum Swaps to Group All 1's Together
| Memory Usage | 18 MB, less than 14.76% of Python3 online submissions for Minimum Swaps to Group All 1's Together
| Datastructures | List[int], Set
| Algorithms | Sliding Window / Two Pointers

### Procedure

1. Create sliding window
2. ...

### Code

#### Option 2: Count the 0's

```python
class Solution:
    def minSwaps(self, data: List[int]) -> int:
        """
        - Maintain a fixed window of size (# of ones).
        - Number of swaps needed = number of zeros in the window.
        """
        # Number of 1's
        window_size = sum(data)
        
        # Number of zeros in first window
        zeros = min_swaps = len(data[:window_size]) - sum(data[:window_size])

        for i in range(window_size, len(data)):
            if data[i - window_size] == 0:
                zeros -= 1
            
            if data[i] == 0:
                zeros += 1
            
            min_swaps = min(min_swaps, zeros)
        return min_swaps
```

#### Option 2: Count the 1's

```python
        window_size = sum(data) # Number of 1's
        one_sum = sum(data[:window_size]) # Num of 1's in first window
        max_ones = one_sum
        for i in range( len(data) - window_size + 1 ):
            if i == 0: continue
            one_sum += ( -data[i-1] + data[i+count-1]) #Update window
            max_ones = max(max_ones, one_sum)
        return window_size - max_ones
```
