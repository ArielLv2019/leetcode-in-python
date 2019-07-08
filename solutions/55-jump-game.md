- [Greedy](#greedy)


# Greedy

```python
class Solution:
    def canJump(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        n = len(nums)
        reach = i = 0

        while i < n and i <= reach:
            reach = max(i+nums[i], reach)
            i += 1

        return i == n
```
