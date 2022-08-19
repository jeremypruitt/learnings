# 659 - Split Array into Consecutive Subsequences

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/split-array-into-consecutive-subsequences/submissions/
| Language | Python 3
| Runtime | 572 ms, faster than 90.02% of Python3 online submissions for Split Array into Consecutive Subsequences
| Memory Usage | 15.2 MB, less than 95.45% of Python3 online submissions for Split Array into Consecutive Subsequences
| Datastructures | List[int]
| Algorithms | Iteration?
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def isPossible(self, nums: List[int]) -> bool:
        sequences, nums_count = defaultdict(int), Counter(nums)
        
        for num in nums:
            # First check if previous num was end of sequence.
            # If so, decrement it as it is no longer end of sequence.
            if sequences[num-1]:
                sequences[num-1] -= 1
            
            # Since we know we are not currently in a seqence,
            # make sure there are at least two more numbers. If 
            # not then we can't build a 3-number sequence.
            elif nums_count[num+1] and nums_count[num+2]:
                nums_count[num+1] -= 1
                nums_count[num+2] -= 1
                
            # If not in a sequnce or if we don't have enough numbers
            # left to make a 3-number sequence, then return False.
            else:
                return False
            
            sequences[num] += 1

        return True
```
