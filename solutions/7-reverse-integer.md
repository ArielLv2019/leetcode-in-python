<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Math](#math)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# Math

```python
class Solution:
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        s = str(x)
        flag = True
        idx = 0
        if s[0] == '-':
            flag = False
            idx += 1

        s = s[idx:][::-1]
        idx = 0
        while idx < len(s) and s[idx] == '0':
            idx += 1

        if idx == len(s): return 0
        ans = int(s[idx:]) if flag else -int(s[idx:])
        if -2 ** 31 < ans < (2 ** 31) - 1:
            return ans

        return 0
```
