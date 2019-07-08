- [Merge Sort](#merge-sort)
- [Insertion Sort](#insertion-sort)


# Merge Sort

Time Complexity: O(nlogn)

```python
class Solution:
    def sortList(self, head):
        if head is None or head.next is None:
            return head
        next = self.split(head)
        return self.merge(self.sortList(head), self.sortList(next))

    def split(self, head):
        prev = None
        slow, fast = head, head
        while fast and fast.next:
            fast = fast.next.next
            prev = slow
            slow = slow.next

        if prev: prev.next = None
        return slow

    def merge(self, head1, head2):
        dummy = ListNode(None)
        node = dummy
        while head1 and head2:
            if head1.val < head2.val:
                node.next = head1
                head1 = head1.next
            else:
                node.next = head2
                head2 = head2.next
            node = node.next

        node.next = head1 or head2
        return dummy.next
```

# Insertion Sort

Time Complexity: O(n^2)

```python
class Solution:
    def sortList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        dummy = ListNode(float('-inf'))
        cur = head
        while cur:
            nxt = cur.next
            nCur, prev = dummy, None
            while nCur and nCur.val < cur.val:
                prev = nCur
                nCur = nCur.next

            cur.next = nCur
            prev.next = cur
            cur = nxt

        return dummy.next
```
