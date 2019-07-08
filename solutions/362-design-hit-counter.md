- [Queue](#queue)
- [Fixed Slots](#fixed-slots)


# Queue

```python
from collections import deque

class HitCounter(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.capacity = 300
        self.queue = deque() # (timestamp, count_of_current_timestamp)
        self.count = 0

    def hit(self, timestamp):
        """
        Record a hit.
        @param timestamp - The current timestamp (in seconds granularity).
        :type timestamp: int
        :rtype: void
        """
        self.getHits(timestamp)
        if self.queue and self.queue[-1][0] == timestamp:
            self.queue[-1][1] += 1
        else:
            self.queue.append([timestamp, 1])
        self.count += 1

    def getHits(self, timestamp):
        """
        Return the number of hits in the past 5 minutes.
        @param timestamp - The current timestamp (in seconds granularity).
        :type timestamp: int
        :rtype: int
        """
        while self.queue and self.queue[0][0] <= timestamp - self.capacity:
            self.count -= self.queue.popleft()[1]
        return self.count

# Your HitCounter object will be instantiated and called as such:
# obj = HitCounter()
# obj.hit(timestamp)
# param_2 = obj.getHits(timestamp)
```

# Fixed Slots

```python
class HitCounter(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.points = [0] * 300
        self.hits = [0] * 300

    def hit(self, timestamp):
        """
        Record a hit.
        @param timestamp - The current timestamp (in seconds granularity).
        :type timestamp: int
        :rtype: void
        """
        idx = timestamp % 300
        if self.points[idx] != timestamp:
            self.points[idx] = timestamp
            self.hits[idx] = 1
        else:
            self.hits[idx] += 1

    def getHits(self, timestamp):
        """
        Return the number of hits in the past 5 minutes.
        @param timestamp - The current timestamp (in seconds granularity).
        :type timestamp: int
        :rtype: int
        """
        ans = 0
        for i in range(300):
            if timestamp - self.points[i] < 300:
                ans += self.hits[i]

        return ans
```
