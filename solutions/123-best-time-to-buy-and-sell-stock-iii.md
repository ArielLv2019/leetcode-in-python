- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming 

Two-pass traversal

```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        if not prices: return 0

        profits = [0] * len(prices)
        maxProfit = 0
        preMin = float('inf')
        for idx, price in enumerate(prices):
            preMin = min(preMin, price)
            maxProfit = max(maxProfit, price - preMin)
            profits[idx] = maxProfit

        totalMax = 0
        maxProfit = 0
        postMax = 0
        for i in range(len(prices) - 1, -1, -1):
            postMax = max(postMax, prices[i])
            maxProfit = max(maxProfit, postMax - prices[i])
            totalMax = max(totalMax, maxProfit + profits[i])

        return totalMax
```
