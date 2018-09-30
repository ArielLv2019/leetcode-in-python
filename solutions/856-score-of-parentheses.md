<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Stack](#stack)
- [Counter](#counter)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Stack

```python
class Solution:
    def scoreOfParentheses(self, S):
        stk = [0]
        for ch in S:
            if ch == '(':
                stk.append(0)
            else:
                last = stk.pop()
                add = last*2 if last > 0 else 1

                # Assumption: input is valid
                stk[-1] += add

        return stk[-1]
```

# Counter

```python
class Solution:
    def scoreOfParentheses(self, S):
        ans = depth = 0
        for idx in range(len(S)):
            if S[idx] == '(':
                depth += 1
            else:
                depth -= 1

            # Assume input is valid
            if S[idx] == ')' and S[idx-1] == '(':
                ans += 1<<depth

        return ans

```
