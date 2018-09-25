<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [String](#string)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# String

```python
class Solution:
    """
    @param str: a string
    @return: return a string
    """
    def reverseWords(self, str):
        def reverse(s, start, end):
            while start < end:
                s[start], s[end] = s[end], s[start]
                start, end = start + 1, end - 1

        lis = list(str)
        reverse(lis, 0, len(lis) - 1)
        last = 0
        for i in range(len(lis)):
            if lis[i] == " ":
                reverse(lis, last, i - 1)
                last = i + 1

        reverse(lis, last, len(lis) - 1)
        return ''.join(lis)
```
