<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Binary Search](#binary-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Binary Search

```python
class Solution(object):
    def findPeakElement(self, nums):
        start, end = 0, len(nums) - 1
        while start < end:
            mid = (start + end) // 2
            if nums[mid] < nums[mid+1]:
                start = mid + 1
            else:
                end = mid
        return start
```
