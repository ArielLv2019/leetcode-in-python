- [Linked List](#Linked-List)

# Linked List

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def rotateRight(self, head: ListNode, k: int) -> ListNode:
        if not head or not head.next:
            return head

        count, itr = 0, head,
        while itr:
            count += 1
            itr = itr.next

        k = k % count
        if k == 0:
            return head

        left = head
        for _ in range(count - k - 1):
            head = head.next
        right = head.next
        head.next = None

        ret = right
        for _ in range(k-1):
            right = right.next
        right.next = left
        return ret       
```
