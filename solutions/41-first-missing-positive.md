# Math

The point is use in-place array as a counter.

```python
class Solution:
    def firstMissingPositive(self, nums):
        nums.append(0)
        n = len(nums)
        for i in range(len(nums)):
            if nums[i] < 0 or nums[i] >= n:
                nums[i] = 0
        for i in range(len(nums)):
            nums[nums[i] % n] += n
        for i in range(0, len(nums)):
            if nums[i] // n == 0:
                return i
        return n
```
