<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Array](#array)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Array 

```python
class Solution:
    def numFriendRequests(self, ages):
        from collections import defaultdict
        count = defaultdict(int)
        for age in ages:
            count[age] += 1

        ans = 0
        for a, ca in count.items():
            for b, cb in count.items():
                if a * 0.5 + 7 >= b or a < b: continue
                ans += ca * cb
                if a == b: ans -= ca

        return ans
```
