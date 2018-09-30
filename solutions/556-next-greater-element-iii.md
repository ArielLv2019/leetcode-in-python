<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [String](#string)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# String

Same idea with [Next Permutation](https://leetcode.com/problems/next-permutation/).

```python
class Solution:
    def nextGreaterElement(self, n):
        """
        :type n: int
        :rtype: int
        """
        nums = [int(ch) for ch in str(n)]
        nxt = self.nextPermutation(nums)
        if not nxt: return -1
        stAns = [str(i) for i in nxt]
        ans = int(''.join(stAns))
        return ans if ans <= 2**31-1 else -1

    def nextPermutation(self, nums):
        sep = 0
        for idx in range(len(nums) - 1, -1, -1):
            if idx > 0 and nums[idx] > nums[idx - 1]:
                sep = idx
                break

        if sep == 0:
            nums[0:] = sorted(nums)
            return None

        minIdx, minItem = -1, float('inf')
        for nIdx, item in enumerate(nums[sep:]):
            if item > nums[sep - 1] and item < minItem:
                minItem, minIdx = item, sep + nIdx

        if minIdx >= 0:
            nums[sep - 1], nums[minIdx] = nums[minIdx], nums[sep - 1]
            nums[sep:] = sorted(nums[sep:])

        return nums
```
