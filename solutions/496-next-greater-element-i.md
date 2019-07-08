- [Traversal from End to Start with Stack](#traversal-from-end-to-start-with-stack)
- [Traversal from Start to End with Stack](#traversal-from-start-to-end-with-stack)


# Traversal from End to Start with Stack

```python
class Solution:
    def nextGreaterElement(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        n = len(nums2)
        greater = {}
        stk = []
        for idx in range(n-1, -1, -1):
            while stk and stk[-1] <= nums2[idx]:
                stk.pop()

            if stk:
                greater[nums2[idx]] = stk[-1]

            stk.append(nums2[idx])

```

# Traversal from Start to End with Stack

```python
class Solution:
    def nextGreaterElement(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        greater = {}
        stk = []
        for nm in nums2:
            while stk and stk[-1] < nm:
                greater[stk.pop()] = nm

            stk.append(nm)

        ans = []
        for nm in nums1:
            ans.append(greater.get(nm, -1))

        return ans
```
