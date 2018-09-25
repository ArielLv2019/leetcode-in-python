<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Recursion](#recursion)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Recursion

```python
class Solution:
    def numberToWords(self, num):
        """
        :type num: int
        :rtype: str
        """
        self.tens = ["Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety"]
        self.ones = ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten",
                     "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen",
                     "Eighteen", "Nineteen"]
        if num == 0:
            return "Zero"
        ret = ""
        if num // 1000000000 != 0:
            ret += self.numberToWords(num // 1000000000) + " Billion "
            num %= 1000000000
        if num // 1000000 != 0:
            ret += self.numberToWords(num // 1000000) + " Million "
            num %= 1000000
        if num // 1000 != 0:
            ret += self.numberToWords(num // 1000) + " Thousand "
            num %= 1000
        if num // 100 != 0:
            ret += self.numberToWords(num // 100) + " Hundred "
            num %= 100
        if num >= 20 and num // 10 != 0:
            ret += self.tens[num // 10 - 2] + " "
            num %= 10
        if num != 0:
            ret += self.ones[num - 1]
            
        return ret.strip()
```
