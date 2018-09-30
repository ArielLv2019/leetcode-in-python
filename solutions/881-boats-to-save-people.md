<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Pointers](#two-pointers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Two Pointers

```python
class Solution:
    def numRescueBoats(self, people, limit):
        people.sort()
        ans = 0
        i, j = 0, len(people) - 1
        while i <= j:
            ans += 1 # This is for j
            if people[i] + people[j] <= limit:
                i += 1
            j -= 1
        return ans
```
