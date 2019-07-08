- [Two Pointers](#two-pointers)


# Two Pointers

```python
class Solution:
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        maxArea = maxHeight = 0
        i, j = 0, len(height) - 1
        while i < j:
            tmpHeight = 0
            if height[i] > height[j]:
                tmpHeight = height[j]
                j -= 1
            else:
                tmpHeight = height[i]
                i += 1

            maxHeight = max(maxHeight, tmpHeight)
            maxArea = max(maxArea, maxHeight*(j-i+1))

        return maxArea

```
