<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Pointers](#two-pointers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Two Pointers

```python
class Solution:
    def compress(self, chars):
        """
        :type chars: List[str]
        :rtype: int
        """
        slow = fast = 0
        n = len(chars)
        while fast < n:
            cur = chars[fast]
            count = 0
            while fast < n and chars[fast] == cur:
                fast += 1
                count += 1

            chars[slow] = cur
            slow += 1
            if count > 1:
                for ch in str(count):
                    chars[slow] = ch
                    slow += 1       
            

        return slow
```
