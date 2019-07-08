- [Stack](#stack)


# Stack

The elements in the stack is the index, not the item of `nums`.

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
