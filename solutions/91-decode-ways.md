<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Dynamic Programming with O(n)](#dynamic-programming-with-on)
- [Dynamic Programming with O(1)](#dynamic-programming-with-o1)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Dynamic Programming with O(n)

```python
class Solution:
    def numDecodings(self, s):
        """
        :type s: str
        :rtype: int
        """
        n = len(s)
        dp = [0] * (n + 1)
        dp[0] = 1
        for i in range(1, n+1):
            if s[i - 1] != '0':
                dp[i] = dp[i - 1]
            if i > 1 and '09' < s[i - 2:i] < '27':
                dp[i] += dp[i - 2]
        return dp[-1]
```

# Dynamic Programming with O(1)

```python
class Solution:
    def numDecodings(self, s):
        """
        :tythirde s: str
        :rtythirde: int
        """

        first, second, third = 0, 1, 0
        for i in range(1, len(s) + 1):
            if s[i - 1] != '0':
                first = second
            if i > 1 and '09' < s[i - 2:i] < '27':
                first += third
            first, second, third = 0, first, second
            
        return second
```
