# 1710 - Maximum Units on a Truck

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/maximum-units-on-a-truck/
| Language | Python 3
| Runtime | 290 ms, faster than 28.67% of Python3 online submissions for Maximum Units on a Truck
| Memory Usage | 14.4 MB, less than 83.07% of Python3 online submissions for Maximum Units on a Truck.
| Datastructures | List[List[int]
| Algorithms | Iterate / Greedy
| Complexity | Time: O(NlogN) Memory: O(1)

### Procedure

1. Sort box types by units, decreasing
2. Loop through sorted box types
3. Determine the number of boxes to load (lowest: truck capacity or the number of boxes of current type)
4. Decrease the truck capacity by the number of boxes we just loaded

### Code

```python
class Solution:
    def maximumUnits(self, boxTypes: List[List[int]], truckSize: int) -> int:
        unitsOnTruck = 0
        for boxType in sorted(boxTypes,key=lambda boxType: boxType[1], reverse=True):
            numberOfBoxes, unitsPerBox = boxType[0], boxType[1]
            numberOfBoxesToLoad = min(truckSize,numberOfBoxes)
            unitsOnTruck += numberOfBoxesToLoad * unitsPerBox
            truckSize -= numberOfBoxesToLoad
        return unitsOnTruck
```
