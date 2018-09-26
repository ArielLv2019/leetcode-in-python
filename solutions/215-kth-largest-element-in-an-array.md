<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Partition](#partition)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
