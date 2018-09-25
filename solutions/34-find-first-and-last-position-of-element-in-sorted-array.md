<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Binary Search](#binary-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
