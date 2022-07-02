# 1465 - Maximum Area of a Piece of Cake After Horizontal and Vertical Cuts

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/maximum-area-of-a-piece-of-cake-after-horizontal-and-vertical-cuts/
| Language | Python 3
| Runtime | 513 ms, faster than 35.66% of Python3 online submissions for Maximum Area of a Piece of Cake After Horizontal and Vertical Cuts
| Memory Usage | 29.2 MB, less than 20.45% of Python3 online submissions for Maximum Area of a Piece of Cake After Horizontal and Vertical Cuts
| Datastructures | List[int]
| Algorithms | Iterate / Sort
| Complexity | Time: O(NlogN+MlogM) Memory: O(1) (N=length of horizontalCuts,M=length of verticalCuts)

### Procedure

1. Sort cuts, adding zero as the first cut
2. Iterate to determine max consecutive gap between two cuts
3. Return product of max length and max breadth, modulus 1e9+7

### Code

#### Option 1: Verbose

```python
class Solution:
    def maxArea(self, h: int, w: int, horizontalCuts: List[int], verticalCuts: List[int]) -> int:
        h = sorted([0] + horizontalCuts + [h])
        w = sorted([0] + verticalCuts   + [w])
        
        x = max(b-a for a,b in zip(h,h[1:]))
        y = max(b-a for a,b in zip(w,w[1:]))
        
        return x*y % (10**9+7) # OR: x*y % int(1e9+7)
        
        # Option 2: Terse (two-liner)
        getMax = lambda arr: max(arr[i] - arr[i-1] for i in range(1,len(arr)))
        return (
            getMax([0]+sorted(horizontalCuts)+[h]) *
            getMax([0]+sorted(verticalCuts)+[w])
        ) % (10**9+7)
```

#### Option 2: Terse (two-liner)

```python
class Solution:
    def maxArea(self, h: int, w: int, horizontalCuts: List[int], verticalCuts: List[int]) -> int:
        getMax = lambda arr: max(arr[i] - arr[i-1] for i in range(1,len(arr)))
        return (
            getMax([0]+sorted(horizontalCuts)+[h]) *
            getMax([0]+sorted(verticalCuts)+[w])
        ) % (10**9+7)
```
