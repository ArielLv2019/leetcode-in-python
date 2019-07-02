- [Sort](#Sort)
- [Priority Queue](#Priority-Queue)

# Sort 

```python
class Solution:
    def carPooling(self, trips: List[List[int]], capacity: int) -> bool:
        start = sorted(map(lambda x: (x[1], x[0]), trips))
        end = sorted(map(lambda x: (x[2], x[0]), trips))

        s_idx = e_idx = 0
        cur_cap = 0
        while s_idx < len(start):
            if start[s_idx][0] < end[e_idx][0]:
                cur_cap += start[s_idx][1]
                if cur_cap > capacity:
                    return False
                s_idx += 1
            else:
                cur_cap -= end[e_idx][1]
                e_idx += 1

        return True
```

# Priority Queue

```python
class Solution:
    def carPooling(self, trips: List[List[int]], capacity: int) -> bool:
        import heapq
        trips = sorted(trips, key=lambda x: x[1])

        in_transit = []
        cur_cap = 0
        for passagers, start, end in trips:
            while in_transit and in_transit[0][0] <= start:
                alight = heapq.heappop(in_transit)
                cur_cap -= alight[1]
            cur_cap += passagers
            if cur_cap > capacity:
                return False
            heapq.heappush(in_transit, (end, passagers))

        return True
```
