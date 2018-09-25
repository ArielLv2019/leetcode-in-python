<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Backtracking](#backtracking)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Backtracking

```python
class Solution:
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        ans = []
        def bt(left, right, prefix):
            if right < left: return
            if left == right == 0:
                ans.append(prefix)

            if left > 0:
                bt(left-1, right, prefix+'(')

            if right > 0:
                bt(left, right-1, prefix+')')

        bt(n, n, '')
        return ans
```
