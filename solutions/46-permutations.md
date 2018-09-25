<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Backtracking](#backtracking)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Backtracking

```python
class Solution:
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        n = len(nums)
        ans = []
        def bt(start):
            if start == n:
                ans.append(nums[:])
                return

            for idx in range(start, n):
                nums[start], nums[idx] = nums[idx], nums[start]
                bt(start+1)
                nums[start], nums[idx] = nums[idx], nums[start]

        bt(0)
        return ans
```
