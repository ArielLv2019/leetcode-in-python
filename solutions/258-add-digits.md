<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Math](#math)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Math

```python
class Solution:
    def addDigits(self, num):
        """
        :type num: int
        :rtype: int
        """
        return 1 + ((num - 1) % 9) if num != 0 else 0
```
