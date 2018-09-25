<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Backtracking](#backtracking)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Backtracking

```python
class Solution:
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []

        def dfs(start, prefix):
            res.append(prefix)
            for i in range(start, len(nums)):
                dfs(i + 1, prefix + [nums[i]])

        dfs(0, [])
        return res
```
