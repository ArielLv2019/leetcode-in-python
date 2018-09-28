<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Dynamic Programming](#dynamic-programming)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Dynamic Programming

```python
class Solution:
    def countBits(self, num):
        """
        :type num: int
        :ans: List[int]
        """
        ans, two = [], None
        for itr in range(num + 1):
            if (itr & itr - 1) == 0:
                if itr == 0:
                    ans.append(0)
                else:
                    ans.append(1)

                two = itr
            elif two:
                ans.append(1 + ans[itr - two])

        return ans
```
