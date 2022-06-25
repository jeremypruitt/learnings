# 121 - Best Time to Buy and Sell Stock

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
| Language | Python 3
| Runtime | 978 ms, faster than 98.26% of Python3 online submissions for Best Time to Buy and Sell Stock
| Memory Usage | 25 MB, less than 85.10% of Python3 online submissions for Best Time to Buy and Sell Stock
| Datastructures | List[int]
| Algorithms | Iterative One Pass
| Complexity | Time: O(n) Memory: O(1)

### Procedure

1. ...

### Code

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        max_profit, min_price = 0, float('inf')
        
        for price in prices:
            # Option 1: min()/max() are easy to read/reason about
            #min_price = min(min_price, price)
            #profit = price - min_price
            #max_profit = max(max_profit, profit)
            
            # Option 2: If statements are faster than min()/max()
            current_profit = price - min_price
            if current_profit > max_profit: max_profit = current_profit
            if price          < min_price:  min_price = price
            
        return max_profit
```
