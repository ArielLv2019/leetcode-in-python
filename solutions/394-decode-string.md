<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Stack](#stack)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Stack

```python
class Solution:
    def decodeString(self, s):
        """
        :type s: str
        :rtype: str
        """
        stk = [["", 1]]
        num = ""
        for ch in s:
            if ch.isdigit():
                num += ch
            elif ch == '[':
                stk.append(["", int(num)])
                num = ""
            elif ch == ']':
                top, k = stk.pop()
                stk[-1][0] += top*k
            else:
                stk[-1][0] += ch

        return stk[0][0]
```
