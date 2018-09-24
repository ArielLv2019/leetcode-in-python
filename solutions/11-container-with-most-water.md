<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Pointers](#two-pointers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
