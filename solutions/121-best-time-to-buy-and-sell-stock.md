- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        preMin = float('inf')
        ans = 0
        for num in prices:
            preMin = min(preMin, num)
            ans = max(ans, num - preMin)

        return ans
```
