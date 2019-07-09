- [Linked List](#Linked-List)

# Linked List

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        dummy = ListNode(float("inf"))
        tail = dummy
        while head:
            if head.val != tail.val:
                tail.next = head
                tail = tail.next
                
            head = head.next
            
        tail.next = None
        return dummy.next
```
