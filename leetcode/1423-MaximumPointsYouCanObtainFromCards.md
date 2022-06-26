# 1423 - Maximum Points You Can Obtain from Cards

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/
| Language | Python 3
| Runtime | 544 ms, faster than 59.98% of Python3 online submissions for Maximum Points You Can Obtain from Cards
| Memory Usage | 27 MB, less than 87.94% of Python3 online submissions for Maximum Points You Can Obtain from Cards
| Datastructures | List[int]
| Algorithms | Sliding Window
| Complexity | Time: O(k) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def maxScore(self, cardPoints: List[int], k: int) -> int:        
        number_of_cards = len(cardPoints)
        sum_of_all_cards = sum(cardPoints)
        sliding_window_size = number_of_cards - k
        sliding_window_sum = sum(cardPoints[:sliding_window_size])
        minimum_sum = sliding_window_sum
        
        for i in range(sliding_window_size, number_of_cards):
            sliding_window_sum += cardPoints[i]
            sliding_window_sum -= cardPoints[i - sliding_window_size]
            minimum_sum = min(minimum_sum, sliding_window_sum)
        
        return sum_of_all_cards - minimum_sum
```
