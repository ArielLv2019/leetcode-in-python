<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Dynamic Programming](#dynamic-programming)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Dynamic Programming

```python
class Solution:
    def minSteps(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 1:
            return 0
        elif n == 2:
            return 2
        elif n % 2 == 0:
            return 2 + self.minSteps(n//2)
        else:
            for i in range(3, n, 2):
                if n % i == 0:
                    return i + self.minSteps(n//i)
            return n
```
