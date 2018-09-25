<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Pointers](#two-pointers)
  - [Solution 1](#solution-1)
  - [Solution 2](#solution-2)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Two Pointers

## Solution 1

```python
class Solution:
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        slow, fast = 0, 0
        while fast < len(nums):
            nums[slow] = nums[fast]
            while fast < len(nums) and nums[fast] == nums[slow]:
                fast += 1
            slow += 1

        return slow
```

## Solution 2

```python
class Solution:
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums: return None
        slow = 0
        for fast in range(1, len(nums)):
            if nums[fast] != nums[slow]:
                slow += 1
                nums[slow] = nums[fast]

        return slow+1
```
