<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Stack](#stack)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Stack

Time Complexity: O(n)
Space Complexity: O(n)

```python
class Solution:
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stk = []
        for item in s:
            if item == '(' or item == '[' or item == '{':
                stk.append(item)
            elif item == ')':
                if not stk or stk[-1] != '(':
                    return False
                else:
                    stk.pop()
            elif item == ']':
                if not stk or stk[-1] != '[':
                    return False
                else:
                    stk.pop()
            elif item == '}':
                if not stk or stk[-1] != '{':
                    return False
                else:
                    stk.pop()

        if stk:
            return False

        return True
```
