<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [String](#string)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# String

```python
class Solution:
    def shiftingLetters(self, S, shifts):
        """
        :type S: str
        :type shifts: List[int]
        :rtype: str
        """
        total = 0
        for idx in range(len(shifts) - 1, -1, -1):
            shifts[idx] += total
            total = shifts[idx]

        ans = ""
        for ch, sf in zip(S, shifts):
            ans += chr((ord(ch) - 97 + sf) % 26 + 97)

        return ans
```
