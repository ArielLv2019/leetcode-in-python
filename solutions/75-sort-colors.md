- [Two Pointers](#two-pointers)


# Two Pointers

```python
class Solution:
    def sortColors(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        if not nums: return

        first, second = 0, len(nums) - 1
        cur = 0
        while cur <= second:
            if nums[cur] == 2:
                nums[second], nums[cur] = nums[cur], nums[second]
                second -= 1
            elif nums[cur] == 0:
                nums[first], nums[cur] = nums[cur], nums[first]
                first += 1
                cur += 1
            else:
                cur += 1
```
