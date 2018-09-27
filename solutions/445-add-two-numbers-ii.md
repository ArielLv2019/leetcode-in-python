<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Cheating](#cheating)
  - [Recursion](#recursion)

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

## Recursion

```python
class Solution:
    def addTwoNumbers(self, l1, l2):
        len1, len2 = self.getLength(l1), self.getLength(l2)
        l1 = self.addLeadingZeros(len2 - len1, l1)
        l2 = self.addLeadingZeros(len1 - len2, l2)
        carry, ans = self.combineList(l1, l2)
        if carry > 0:
            l3 = ListNode(carry)
            l3.next = ans
            ans = l3
        return ans

    def getLength(self, node):
        l = 0
        while node:
            l += 1
            node = node.next
        return l

    def addLeadingZeros(self, n, node):
        for i in range(n):
            new = ListNode(0)
            new.next = node
            node = new
        return node

    def combineList(self, l1, l2):
        if (not l1 and not l2):
            return (0, None)
        c, new = self.combineList(l1.next, l2.next)
        s = l1.val + l2.val + c
        ans = ListNode(s % 10)
        ans.next = new
        return (s // 10, ans)
```
