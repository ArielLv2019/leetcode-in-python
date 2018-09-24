<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Dynamic Programming](#dynamic-programming)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Dynamic Programming

```python
class Solution:
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        memo = {}

        def dp(i, j):
            if (i, j) not in memo:
                ans = False
                if i == len(s) and j == len(p):
                    ans = True

                if j < len(p):
                    first = i < len(s) and (p[j] == s[i] or p[j] == '.')
                    if j + 1 < len(p) and p[j+1] == '*':
                        ans = dp(i, j+2) or (first and dp(i+1, j))
                    else:
                        ans = first and dp(i+1, j+1)

                memo[(i, j)] = ans

            return memo[(i, j)]

        return dp(0, 0)
```
