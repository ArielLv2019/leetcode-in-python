- [Dynamic Programming](#dynamic-programming)


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
