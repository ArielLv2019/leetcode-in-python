- [One-pass Hash Table with Two Pointers](#One-pass-Hash-Table-with-Two-Pointers)


# One-pass Hash Table with Two Pointers

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        used = {}
        ans = start = 0
        for i, c in enumerate(s):
            if c in used and start <= used[c]:
                start = used[c] + 1
            else:
                ans = max(ans, i - start + 1)

            used[c] = i

        return ans
```

The reason we use `start <= used[c]` to limit the movement of `start` is for the cases like "tmmzuxt", which may move the `start` again when it visits the trailing "t". 

It's wrong if we try to do this in the `for` loop. Obviously it is against "tmmzuxt" too.

```python
if c not in used:
    ans = max(ans, i - start + 1)
elif start <= used[c]:
    start = used[c] + 1
```
