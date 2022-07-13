# 1268 - Search Suggestions System

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/search-suggestions-system/
| Language | Python 3
| Runtime | 568 ms, faster than 25.14% of Python3 online submissions for Search Suggestions System
| Memory Usage | 17.1 MB, less than 55.63% of Python3 online submissions for Search Suggestions System
| Datastructures | List[str]
| Algorithms | Sort + Binary Search
| Complexity | Time: O(NlogN+MlogN) Memory: O(logN) (N=number of elements in products, M=length of searchWord)

### Procedure

1. ...

### Code

```python
class Solution:
    def suggestedProducts(self, products: List[str], searchWord: str) -> List[List[str]]:
        products.sort()
        result = []
        
        for i in range( len(searchWord) ):
            current = []
            for product in products:
                if product.startswith(searchWord[:i+1]):
                    current.append(product)
            
            result.append(current[:3])
        
        return result
```
