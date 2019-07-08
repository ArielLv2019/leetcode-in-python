- [Dynamic Programming](#dynamic-programming)


# Dynamic Programming

```python
class Solution:
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums: return 0
        sumLeft = ans = float('-inf')
        for i in nums:
            sumLeft = max(sumLeft + i, i)
            ans = max(ans, sumLeft)

        return ans
```
