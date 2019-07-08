- [Linked List](#linked-list)


# Linked List

```python
class Solution:
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        dummy = ListNode(0)
        cur = head
        while cur:
            tmp = cur.next
            cur.next = dummy.next
            dummy.next = cur
            cur = tmp

        return dummy.next
```
