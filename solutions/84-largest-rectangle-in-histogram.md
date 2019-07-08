- [Stack](#stack)


# Stack

The stack stores the increasing heights that ends with current height.

```python
class Solution:
    def largestRectangleArea(self, heights):
        """
        :type heights: List[int]
        :rtype: int
        """
        stk = []
        ans = 0
        heights.append(0)
        for i in range(len(heights)):
            leftIdx = i
            while stk and stk[-1][0] >= heights[i]:
                leftHeight, leftIdx = stk.pop()
                ans = max(ans, heights[i]*(i+1-leftIdx), leftHeight*(i-leftIdx))

            stk.append((heights[i], leftIdx))

        return ans
```
