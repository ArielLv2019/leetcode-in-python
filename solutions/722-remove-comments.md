<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [String](#string)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# String

```python
class Solution:
    def removeComments(self, source):
        inBlock = False
        ans, newLine = [], []
        for line in source:
            idx = 0
            if not inBlock:
                newLine = []

            while idx < len(line):
                if line[idx:idx+2] == '/*' and not inBlock:
                    inBlock = True
                    idx += 1
                elif line[idx:idx+2] == '*/' and inBlock:
                    inBlock = False
                    idx += 1
                elif line[idx:idx+2] == '//' and not inBlock :
                    break
                elif not inBlock:
                    newLine.append(line[idx])

                # step forward even the above conditions are all false
                # which means in block
                idx += 1

            if newLine and not inBlock:
                ans.append(''.join(newLine))

        return ans
```
