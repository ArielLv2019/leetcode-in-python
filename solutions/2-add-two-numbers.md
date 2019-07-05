- [Linked List](#linked-list)


# Linked List

```python
class Solution:
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        add = 0
        cur1, cur2 = l1, l2
        tail = l1
        while cur1 and cur2:
            cur1.val += cur2.val + add
            if cur1.val >= 10:
                add = 1
                cur1.val -= 10
            else:
                add = 0

            tail = cur1
            cur1, cur2 = cur1.next, cur2.next

        tmpCur = cur1 or cur2
        if tmpCur:
            tail.next = tmpCur
            while tmpCur:
                tmpCur.val += add
                if tmpCur.val >= 10:
                    add = 1
                    tmpCur.val -= 10
                else:
                    add = 0

                tail, tmpCur = tmpCur, tmpCur.next

        if add:
            node = ListNode(add)
            tail.next = node

        return l1
```
