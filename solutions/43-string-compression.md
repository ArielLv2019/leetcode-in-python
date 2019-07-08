- [Two Pointers](#two-pointers)


# Two Pointers

```python
class Solution:
    def compress(self, chars):
        """
        :type chars: List[str]
        :rtype: int
        """
        slow = fast = 0
        n = len(chars)
        while fast < n:
            cur = chars[fast]
            count = 0
            while fast < n and chars[fast] == cur:
                fast += 1
                count += 1

            chars[slow] = cur
            slow += 1
            if count > 1:
                for ch in str(count):
                    chars[slow] = ch
                    slow += 1       
            

        return slow
```
