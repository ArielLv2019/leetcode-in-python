- [Two Pointers](#two-pointers)


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

            if fast and fast == slow:
                cycle = True
                break

        if cycle:
            while head != slow:
                head = head.next
                slow = slow.next
            return head

        return None
```
