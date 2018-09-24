<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Math](#math)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# Math

```python
class Solution:
    def myAtoi(self, str):
        """
        :type str: str
        :ans: int
        """
        if not str:
            return 0

        start = 0
        while start < len(str) and str[start] == ' ':
            start += 1

        if start == len(str): return 0

        flag = True
        if str[start] == '-':
            start += 1
            flag = False
        elif str[start] == '+':
            start += 1

        ans = 0
        for ch in str[start:]:
            num = ord(ch) - ord('0')
            if 0 <= num <= 9:
                ans = 10 * ans + num
            else:
                return self.comp(ans, flag)

        return self.comp(ans, flag)

    def comp(self, ans, flag):
        signedNum = (ans if flag else ans * (-1))
        if signedNum > 2147483647:
            return 2147483647
        elif signedNum < -2147483648:
            return -2147483648
        else:
            return signedNum
```
