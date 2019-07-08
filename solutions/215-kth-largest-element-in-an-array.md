- [Partition](#partition)


# Partition

```python
class Solution:
    def findKthLargest(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        n = len(nums)
        target = n - k
        def partition(start, end):
            left, right = start, end
            tmp = nums[left]
            while left < right:
                while left < right and nums[right] >= tmp:
                    right -= 1
                nums[left] = nums[right]

                while left < right and nums[left] <= tmp:
                    left += 1
                nums[right] = nums[left]

            nums[left] = tmp
            return left

        idx = partition(0, n-1)
        while idx != target:
            if idx < target:
                idx = partition(idx+1, n-1)
            elif idx > target:
                idx = partition(0, idx-1)

        return nums[idx]
```
