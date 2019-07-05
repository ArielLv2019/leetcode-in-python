- [Two Pointers](#Two-Pointers)


# Two Pointers

```python
class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        slow = fast = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next

            if fast and fast == slow:
                return True

        return False
```
