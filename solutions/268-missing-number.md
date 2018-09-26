<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Sum](#sum)
- [XOR](#xor)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Sum

```python
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        return n * (n+1)/2 - sum(nums) if n > 0 else 0
```

# XOR

```python
class Solution:
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ans = len(nums)
        for i in range(len(nums)):
            ans ^= i
            ans ^= nums[i]

        return ans
```
