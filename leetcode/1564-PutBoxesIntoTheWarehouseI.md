# 1564 - Put Boxes Into the Warehouse I

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/put-boxes-into-the-warehouse-i/
| Language | Python 3
| Runtime | 741 ms, faster than 62.03% of Python3 online submissions for Put Boxes Into the Warehouse I
| Memory Usage | 33.2 MB, less than 35.44% of Python3 online submissions for Put Boxes Into the Warehouse I
| Datastructures | List[int]
| Algorithms | Greedy
| Complexity | Time: O(NlogN+M) Memory: O(1) (N=number of boxes, M=number of warehouses)

### Procedure

1. ...

### Code

```python
class Solution:
    def maxBoxesInWarehouse(self, boxes: List[int], warehouse: List[int]) -> int:
        boxes.sort()
        number_of_warehouses = len(warehouse)
        number_of_boxes = len(boxes)
        result = 0
        
        for i in range(number_of_boxes-1, -1, -1):
            if boxes[i] <= warehouse[result]:
                result += 1
                if result == number_of_warehouses:
                    return number_of_warehouses
        
        return result
```
