```python
class Solution:
    def constructMaximumBinaryTree(self, nums):
        """
        :type nums: List[int]
        :rtype: TreeNode
        """
        def construct(start, end):
            if start >= end:
                return None

            maxIdx = start
            for idx in range(start, end):
                if nums[maxIdx] < nums[idx]:
                    maxIdx = idx

            root = TreeNode(nums[maxIdx])
            root.left = construct(start, maxIdx)
            root.right = construct(maxIdx + 1, end)

            return root

        return construct(0, len(nums))
```
