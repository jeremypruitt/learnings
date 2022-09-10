# 188 - Best Time to Buy and Sell Stock IV

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/
| Language | Python 3
| Runtime | 223 ms, faster than 46.91% of Python3 online submissions for Best Time to Buy and Sell Stock IV
| Memory Usage | 13.9 MB, less than 79.28% of Python3 online submissions for Best Time to Buy and Sell Stock IV
| Datastructures | DS Table, List[int]
| Algorithms | Group + Least Common Prefix?
| Complexity | Time: O(KN) Memory: O(K)

### Procedure

1. ...

### Code

#### Option 1

```python
class Solution:
    def maxProfit(self, k: int, prices: List[int]) -> int:
        """
        :type k: int
        :type prices: List[int]
        :rtype: int
        """
        buy  = [inf] * (k + 1)
        sell = [0]   * (k + 1)
        
        for price in prices:
            for k in range(1, k+1):
                buy[k]  = min(buy[k],  price - sell[k-1])
                sell[k] = max(sell[k], price - buy[k])
        
        return sell[-1]
```

#### Option 2

```python
class Solution:
    def maxProfit(self, k: int, prices: List[int]) -> int:
        """
        :type k: int
        :type prices: List[int]
        :rtype: int
        """
        n_prices = len(prices)
        if not prices or k == 0 or n_prices < 2: return 0
        
        if k >= n_prices // 2:
            return sum(first - last
                       for first, last in zip(prices[1:], prices[:-1])
                       if first > last)
        
        profits = [0] * n_prices
        
        for _ in range(k):
            preprofit = 0
            for i in range(1,n_prices):
                profit = prices[i] - prices[i-1]
                preprofit = max(preprofit+profit, profits[i])
                profits[i] = max(profits[i-1], preprofit)
    
        return profits[-1]
```
