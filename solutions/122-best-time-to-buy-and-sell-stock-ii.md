- [Greedy](#greedy)


# Greedy

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
            if preMin < num:
                ans += num - preMin

            preMin = num

        return ans
```
