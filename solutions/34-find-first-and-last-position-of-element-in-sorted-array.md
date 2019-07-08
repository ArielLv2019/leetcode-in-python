- [Binary Search](#binary-search)


# Binary Search

```python
class Solution:
    def searchRange(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """

        def lowerBound(start, end):
            if not nums:
                return -1

            while start < end:
                mid = int((start + end) / 2)
                if nums[mid] < target:
                    start = mid + 1
                else:
                    end = mid
            return start if nums[start] == target else -1

        left = lowerBound(0, len(nums) - 1)
        if left == -1:
            return [-1, -1]
        else:
            right = left
            while right < len(nums) and nums[right] == target:
                right += 1
            return [left, right - 1]
```
