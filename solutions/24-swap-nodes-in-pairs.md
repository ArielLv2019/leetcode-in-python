<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Split](#split)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Split 

```python
class Solution:
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next: return head
        flag = True
        odd = ListNode(0)
        even = ListNode(0)
        oddTail, evenTail = odd, even
        cur = head
        while cur:
            if flag:
                oddTail.next = cur
                oddTail = cur
            else:
                evenTail.next = cur
                evenTail = cur

            cur, flag = cur.next, not flag

        oddTail.next = evenTail.next = None
        oddItr, evenItr = odd.next, even.next
        dummy = ListNode(0)
        tail = dummy
        while evenItr and oddItr:
            tail.next = evenItr
            tail = evenItr
            evenItr = evenItr.next

            tail.next = oddItr
            tail = oddItr
            oddItr = oddItr.next

        return dummy.next
```
