- [Linked List](#linked-list)


# Linked List

```python
class Solution(object):
    def getIntersectionNode(self, headA, headB):
        """
        :type head1, head1: ListNode
        :rtype: ListNode
        """
        curA, curB = headA, headB
        lenA, lenB = 0, 0
        while curA:
            lenA += 1
            curA = curA.next
        while curB:
            lenB += 1
            curB = curB.next
        curA, curB = headA, headB
        if lenA > lenB:
            for i in range(lenA - lenB):
                curA = curA.next
        elif lenB > lenA:
            for i in range(lenB - lenA):
                curB = curB.next
        while curB != curA:
            curB = curB.next
            curA = curA.next
        return curA
```
