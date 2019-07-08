- [Binary Search](#binary-search)


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
