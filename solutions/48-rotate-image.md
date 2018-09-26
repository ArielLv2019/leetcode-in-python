<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Flips](#two-flips)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Two Flips

```python
class Solution:
    def rotate(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: void Do not return anything, modify matrix in-place instead.
        """
        for row in range(len(matrix) // 2):
            for col in range(len(matrix[0])):
                matrix[row][col], matrix[len(matrix) -1 - row][col] = \
                matrix[len(matrix) - 1 - row][col], matrix[row][col]


        for col in range(0, len(matrix[0])):
            for row in range(0, col):
                matrix[row][col], matrix[col][row] = \
                matrix[col][row], matrix[row][col]
```
