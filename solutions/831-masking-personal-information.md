- [String](#string)


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
