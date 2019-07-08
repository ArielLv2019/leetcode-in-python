- [Binary Search](#binary-search)
- [Heap](#heap)


# Binary Search

```python
class Solution:
    def kthSmallest(self, matrix, k):
        m, n = len(matrix), len(matrix[0])
        low, high = matrix[0][0], matrix[-1][-1]
        while low <= high:
            mid = (low + high) // 2

            count = 0
            j = n - 1
            for i in range(m):
                while j >= 0 and matrix[i][j] > mid:
                    j -= 1
                count += j + 1

            if count < k:
                low = mid + 1
            else:
                high = mid - 1

        return low
```

# Heap

Time Complexity: O(klogk)
Space Complexity: O(n)

```python
class Solution:
    def kthSmallest(self, matrix, k):
        """
        :type matrix: List[List[int]]
        :type k: int
        :rtype: int
        """
        from heapq import heappop, heappush
        hp = [(row[0], i, 0) for i, row in enumerate(matrix)]
        ans = 0
        for _ in range(k):
            ans, i, j = heappop(hp)
            if j + 1 < len(matrix[0]):
                heappush(hp, (matrix[i][j+1], i, j+1))

        return ans
```
