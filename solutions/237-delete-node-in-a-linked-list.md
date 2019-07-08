- [Shift](#shift)


# Shift

```python
class Solution:
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        pre = node
        while node.next:
            node.val = node.next.val
            pre = node
            node = node.next

        pre.next = None
```
