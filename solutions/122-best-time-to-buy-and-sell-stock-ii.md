<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Greedy](#greedy)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Greedy

```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        preMin = float('inf')
        ans = 0
        for num in prices:
            if preMin < num:
                ans += num - preMin

            preMin = num

        return ans
```
