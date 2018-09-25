<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Dynamic Programming](#dynamic-programming)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Dynamic Programming

```python
class Solution:
    def longestValidParentheses(self, s):
        if not s or len(s) < 2:
            return 0

        stack = []
        leftmost = -1
        ans = 0
        for i in range(len(s)):
            if s[i] == '(':
                stack.append(i)
            else:  # case ')'
                if not stack:  # ) is more
                    leftmost = i
                else:
                    stack.pop()
                    if not stack:  # ( and ) match
                        ans = max(ans, i - leftmost)
                    else:  # ( is more
                        ans = max(ans, i - stack[-1])
        return ans
```
