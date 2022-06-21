# 1642 - Furthest Building You Can Reach

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/furthest-building-you-can-reach/
| Language | Python 3
| Runtime | 762 ms, faster than 62.52% of Python3 online submissions for Furthest Building You Can Reach
| Memory Usage | 28.5 MB, less than 89.32% of Python3 online submissions for Furthest Building You Can Reach
| Datastructures | minheap, List[int]
| Algorithms | Min-Heap
| Complexity | Time: O(NlogL) Memory: O(L) (N=number of buildings, L=number of ladders)

### Procedure

1. ...

### Code

#### Option 1: Verbose

```python
class Solution:
    def furthestBuilding(self, heights: List[int], bricks: int, ladders: int) -> int:
        height_diffs = []
        for i, curr_height in enumerate(heights):
            # Grab next & last index number for readability:
            next_i, last_i = i + 1, len(heights) - 1
            
            # Check to see if we are on last building:
            if next_i > last_i: return i
            
            # Get height of the next building and the diff
            # in height between current and next building:
            next_height = heights[next_i]
            height_diff = next_height - curr_height
                        
            # If the next building is same or short,
            # continue to next iteration:
            if height_diff <= 0: continue
            
            # Add height diff to heap of height diffs:
            heappush(height_diffs, height_diff)
            
            # If more height diffs than ladders, pop the shortest
            # height diff from the heap and span it with bricks:
            if len(height_diffs) > ladders:
                bricks -= heappop(height_diffs)
            
            # If spanning the height_diff results in negative
            # number of bricks, then we are done:
            if bricks < 0: return i
```

#### Option 2: Terse

```python
class Solution:
    def furthestBuilding(self, heights: List[int], bricks: int, ladders: int) -> int:
        height_diffs = []
        for i in range( len(heights) - 1 ):
            height_diff = heights[i+1] - heights[i]
            if height_diff <= 0: continue
            
            heappush(height_diffs, height_diff)
            if len(height_diffs) > ladders:
                bricks -= heappop(height_diffs)
            
            if bricks < 0: return i
        
        return len(heights) - 1
```
