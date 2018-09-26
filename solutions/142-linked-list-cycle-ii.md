<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Two Pointers](#two-pointers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Two Pointers

```python
class Solution(object):
    def detectCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        slow = fast = head
        cycle = False
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next

            if fast and slow and fast == slow:
                cycle = True
                break

        if cycle:
            while head != slow:
                head = head.next
                slow = slow.next
            return head

        return None
```
