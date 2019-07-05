- [Hash Table + Linked List](#hash-table--linked-list)


# Hash Table + Linked List

```python
class Node:
    def __init__(self, k, v):
        self.key = k
        self.val = v
        self.prev = None
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = Node(0, 0)
        self.tail = Node(0, 0)
        self.head.next = self.tail
        self.tail.prev = self.head

    def remove(self, node):
        p = node.prev
        n = node.next
        p.next = n
        n.prev = p

    def removeTail(self):
        node = self.tail.prev
        if node != self.head:
            self.remove(node)
            return node

        return None

    def add(self, node):
        node.next = self.head.next
        node.prev = self.head
        node.next.prev = node
        self.head.next = node


class LRUCache:
    def __init__(self, capacity):
        self.capacity = capacity
        self.lookup = {}
        self.list = LinkedList()

    def get(self, key):
        if key in self.lookup:
            n = self.lookup[key]
            self.list.remove(n)
            self.list.add(n)
            return n.val

        return -1

    def put(self, key, value):
        if key in self.lookup:
            self.list.remove(self.lookup[key])

        n = Node(key, value)
        self.list.add(n)
        self.lookup[key] = n
        if len(self.lookup) > self.capacity:
            node = self.list.removeTail()
            if node:
                del self.lookup[node.key]
            
# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```
