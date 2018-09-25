<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Cheating](#cheating)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Cheating

```python
class Solution:
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        x1, x2 = 0, 0
        while l1:
            x1 = x1 * 10 + l1.val
            l1 = l1.next
        while l2:
            x2 = x2 * 10 + l2.val
            l2 = l2.next
        x = x1 + x2

        dummy  = ListNode(0)
        if x == 0: return dummy
        while x:
            v, x = x % 10, x // 10
            newNode = ListNode(v)
            newNode.next = dummy.next
            dummy.next = newNode

        return dummy.next
```
