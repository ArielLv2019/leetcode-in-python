<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Stack](#stack)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Stack

```python
class Solution:
    def sumSubarrayMins(self, A):
        MOD = 10**9 + 7

        stk = []
        ans = prod = 0
        for x in A:
            count = 1
            while stk and stk[-1][0] >= x:
                y, c = stk.pop()
                prod -= y * c
                count += c

            stk.append((x, count))
            prod += x * count
            ans += prod

        return ans % MOD
```
