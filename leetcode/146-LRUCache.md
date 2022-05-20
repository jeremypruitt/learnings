# 146 - LRU Cache

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/lru-cache/
| Language | Python 3
| Runtime | 1244 ms, faster than 35.29% of Python3 online submissions for LRU Cache
| Memory Usage | 76.6 MB, less than 9.61% of Python3 online submissions for LRU Cache
| Datastructures | set, matrix
| Algorithms | DFS, recursion

### Procedure

1. TBD...

### Code


```python
class Node:
    def __init__(self, key: int, val: int, prev=None, next=None) -> None:
        self.key = key
        self.val = val
        self.prev = self.next = None

class LRUCache:
    def __init__(self, capacity: int) -> None:
        self.capacity = capacity
        self.seen = {}
        
        self.left = Node(0,0)
        self.right = Node(0,0)
        self.left.next = self.right
        self.right.prev = self.left
        
    def get(self, key: int) -> int:
        if key in self.seen:
            self.remove(self.seen[key])
            self.add(self.seen[key])
            return self.seen[key].val
        return -1

    def put(self, key: int, value: int) -> None:
        if key in self.seen:
            self.remove(self.seen[key])
        self.seen[key] = Node(key, value)
        self.add(self.seen[key])
        
        if len(self.seen) > self.capacity:
            lru = self.left.next
            self.remove(lru)
            del self.seen[lru.key]
        
    def remove(self, node: Node) -> None:
        node.prev.next = node.next
        node.next.prev = node.prev

    def add(self, node: Node) -> None:
        node.prev = self.right.prev
        node.next = self.right
        self.right.prev.next = node
        self.right.prev = node
```
