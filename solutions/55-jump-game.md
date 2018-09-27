<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Greedy](#greedy)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Greedy

```python
class Solution:
    def canJump(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        n = len(nums)
        reach = i = 0

        while i < n and i <= reach:
            reach = max(i+nums[i], reach)
            i += 1

        return i == n
```
