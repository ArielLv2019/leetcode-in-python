<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [String](#string)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# String

```python
class Solution:
    def orderlyQueue(self, S, K):
        """
        :type S: str
        :type K: int
        :rtype: str
        """
        if K == 1:
            return min(S[i:] + S[:i] for i in range(len(S)))
        return "".join(sorted(S))
```
