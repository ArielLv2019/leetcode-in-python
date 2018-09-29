<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Stack](#stack)
- [Stack](#stack-1)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Stack

The elements in the stack is the index, not the item of `nums`.

# Stack

```python
class Solution:
    def nextGreaterElements(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        n = len(nums)
        stk = []
        ans = [-1] * n
        for idx in range(2*n):
            lowIdx = idx % n
            while stk and nums[stk[-1]] < nums[lowIdx]:
                ans[stk.pop()] = nums[lowIdx]

            stk.append(lowIdx)

        return ans
```
