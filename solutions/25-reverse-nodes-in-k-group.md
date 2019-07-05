- [Linked List](#Linked-List)


# Linked List

```python
class Solution:
    def reverseKGroup(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        newHead = newEnd = ListNode(0)
        cur = head
        while cur:
            first, cnt = cur, 1
            while cnt < k and cur:
                cur, cnt = cur.next, cnt + 1
            if cnt == k and cur:
                cur, prev = first, None

                for _ in range(k):
                    # prev, cur.next, cur = cur, prev, cur.next

                    tmp = cur.next
                    cur.next = prev
                    prev = cur
                    cur = tmp

                newEnd.next, newEnd = prev, first
            else:
                newEnd.next = first

        return newHead.next
```
