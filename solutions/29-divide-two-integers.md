<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Binary Search](#binary-search)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Binary Search

```python
class Solution:
    def divide(self, dividend, divisor):
        """
        :type dividend: int
        :type divisor: int
        :rtype: int
        """
        if not divisor or (dividend == -pow(2, 31) and divisor == -1):
            return pow(2, 31) - 1

        sign = False if ((divisor < 0) ^ (dividend < 0)) else True
        dvd, dvs = abs(dividend), abs(divisor)
        res = 0
        while dvd >= dvs:
            tmp = dvs
            multiple = 1
            while dvd >= (tmp << 1):
                tmp <<= 1
                multiple <<= 1

            dvd -= tmp
            res += multiple

        return res if sign else -res
```
