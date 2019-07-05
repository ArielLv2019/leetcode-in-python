- [Split](#Split)


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

        oddTail.next = evenTail.next = None # This is very important!
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
