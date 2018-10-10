<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Backtracking](#backtracking)
- [Bit Manipulation](#bit-manipulation)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Backtracking

```python
class Solution:
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        ans = []

        def dfs(start, prefix):
            ans.append(prefix)
            for i in range(start, len(nums)):
                dfs(i + 1, prefix + [nums[i]])

        dfs(0, [])
        return ans
```

# Bit Manipulation

```python
class Solution:
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        ans = []
        for i in range(1<<len(nums)):
            tmp = []
            for j in range(len(nums)):
                if i & (1 << j):
                    tmp.append(nums[j])
            ans.append(tmp)
        
        return ans
```
