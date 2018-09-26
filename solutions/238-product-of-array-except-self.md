```python
class Solution:
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        pdt = 1
        zero = 0
        for x in nums:
            if x:
                pdt *= x
            else:
                zero += 1

        ret = [pdt] * len(nums)
        for idx, x in enumerate(nums):
            if x == 0 and zero > 1:
                ret[idx] = 0

            if x != 0 and zero < 1:
                ret[idx] = int(ret[idx] / x)
            elif x != 0 and zero > 0:
                ret[idx] = 0

        return ret
```
