<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Linked List](#linked-list)
- [Hash Table](#hash-table)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Linked List

Construct A -> A' -> B -> B' firstly.

```python
class Solution(object):
    def copyRandomList(self, head):
        """
        :type head: RandomListNode
        :rtype: RandomListNode
        """
        # construct duplicated list
        cur = head
        while cur:
            newNode = RandomListNode(cur.label)
            newNode.next = cur.next
            cur.next = newNode
            cur = cur.next.next

        # assign random
        cur = head
        while cur:
            tmp = cur.next.next
            new = cur.next

            if cur.random:
                new.random = cur.random.next

            cur = tmp

        # split list
        dummy = None
        cur = head
        while cur:
            tmp = cur.next.next
            new = cur.next
            if not dummy: dummy = new

            cur.next = tmp
            if tmp:
                new.next = tmp.next

            cur = tmp

        return dummy
```

# Hash Table

```python
class Solution(object):
    def __init__(self):
        self.visited = {}

    def getClonedNode(self, node):
        if node:
            if node in self.visited:
                return self.visited[node]
            else:
                self.visited[node] = RandomListNode(node.label)
                return self.visited[node]
        return None

    def copyRandomList(self, head):
        """
        :type head: RandomListNode
        :rtype: RandomListNode
        """

        if not head:
            return head

        old_node = head
        new_node = RandomListNode(old_node.label)
        self.visited[old_node] = new_node

        while old_node != None:
            new_node.random = self.getClonedNode(old_node.random)
            new_node.next = self.getClonedNode(old_node.next)

            old_node = old_node.next
            new_node = new_node.next

        return self.visited[head]
```
