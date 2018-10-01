<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [String](#string)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# String

```python
class Solution(object):
    def maskPII(self, S):
        if '@' in S:
            userName, domain = S.split('@')
            return ('%s*****%s@%s' % (userName[0], userName[-1], domain)).lower()
        else:
            digits = ''.join(list(filter(lambda x:x.isdigit(), S)))
            local = '***-***-%s' % digits[-4:]
            if len(digits) == 10:
                return local
            return '+%s-%s' % ('*' * (len(digits) - 10), local)
```
