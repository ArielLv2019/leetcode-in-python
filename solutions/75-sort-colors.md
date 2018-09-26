<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Pointers](#two-pointers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
