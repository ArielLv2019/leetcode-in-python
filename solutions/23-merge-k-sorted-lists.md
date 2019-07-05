- [Heap](#heap)


# Heap

```python
class Element:
    def __init__(self, node):
        self.node = node

    def __cmp__(self, other):
        return self.node.val - other.node.val

class Solution:
    def mergeKLists(self, lists):
        """
        :type lists: List[ListNode]
        :rtype: ListNode
        """
        from heapq import heappop, heappush
        hp = []
        for lis in lists:
            if lis:
                heappush(hp, Element(lis))

        dummy = ListNode(0)
        tail = dummy
        while hp:
            ele = heappop(hp)
            node = ele.node
            tail.next = node
            tail = node
            if node.next:
                heappush(hp, Element(node.next))

        return dummy.next
```
