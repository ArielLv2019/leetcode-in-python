<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Stack](#stack)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Stack

```python
class Solution:
    def simplifyPath(self, path):
        """
        :type path: str
        :rtype: str
        """
        stk = []
        for dir in path.split("/"):
            if not dir or dir == '.':
                continue
            elif dir == '..':
                if stk:
                    stk.pop()
            else:
                stk.append(dir)

        return "/%s" % '/'.join(stk) if stk else "/"
```
