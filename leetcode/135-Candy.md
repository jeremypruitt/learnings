# 135 - Candy

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/candy/
| Language | Python 3
| Runtime | 263 ms, faster than 42.85% of Python3 online submissions for Candy
| Memory Usage | 16.8 MB, less than 37.74% of Python3 online submissions for Candy
| Datastructures | List[int]
| Algorithms | Two-Pass, One-Array
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def candy(self, ratings: List[int]) -> int:
        number_of_children = len(ratings)
        if number_of_children == 0: return 0
        
        # Every child gets at least 1 candy
        candies = [1] * number_of_children
        
        # Determine candies based on the previous child. Range
        # starts at 1 because element 0 has no previous child.
        for current_child in range(1, number_of_children):
            previous_child = current_child - 1
            if ratings[current_child] > ratings[previous_child]:
                candies[current_child] = candies[previous_child] + 1
        
        # Determine candies based on the next child. Range ends
        # early because no next child after last element.
        for current_child in range(number_of_children-2,-1,-1):
            next_child = current_child + 1
            if ratings[current_child] > ratings[next_child]:
                candies[current_child] = max(candies[current_child], candies[next_child] + 1)
        
        return sum(candies)
```
