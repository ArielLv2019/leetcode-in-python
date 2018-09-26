<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Shift](#shift)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Shift

```python
class Solution:
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        pre = node
        while node.next:
            node.val = node.next.val
            pre = node
            node = node.next

        pre.next = None
```
