- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def minCostClimbingStairs(self, cost):
        """
        :type cost: List[int]
        :rtype: int
        """
        f1, f2 = cost[0], cost[1]
        for i in cost[2:]:
            f1, f2 = f2, min(f1, f2) + i

        return min(f1, f2)
```
