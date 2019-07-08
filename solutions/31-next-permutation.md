- [Array](#array)


# Array

```python
class Solution:
    def nextPermutation(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        sep = 0
        for idx in range(len(nums) - 1, -1, -1):
            if idx > 0 and nums[idx] > nums[idx - 1]:
                sep = idx
                break

        if sep == 0:
            nums[0:] = sorted(nums)
            return

        minIdx, minItem = -1, float('inf')
        for nIdx, item in enumerate(nums[sep:]):
            if item > nums[sep-1] and item < minItem:
                    minItem, minIdx = item, sep + nIdx

        if minIdx >= 0:
            nums[sep - 1], nums[minIdx] = nums[minIdx], nums[sep - 1]
            nums[sep:] = sorted(nums[sep:])
```
