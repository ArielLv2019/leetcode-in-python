- [Hash Table](#hash-table)
- [One-pass](#one-pass)


# Hash Table

```python
class Solution:
    """
    @param s: the given string
    @return: if a permutation of the string could form a palindrome
    """
    def canPermutePalindrome(self, s):
        # write your code here
        from collections import defaultdict
        counter = defaultdict(int)
        for ch in s:
            counter[ch] += 1

        ans = 0
        for v in counter.values():
            ans += v % 2

        return ans <= 1
```

# One-pass

```python
class Solution:
    """
    @param s: the given string
    @return: if a permutation of the string could form a palindrome
    """
    def canPermutePalindrome(self, s):
        # write your code here
        from collections import defaultdict
        counter = defaultdict(int)
        ans = 0
        for ch in s:
            counter[ch] += 1
            if counter[ch] % 2 == 0:
                ans -= 1
            else:
                ans += 1

        return ans <= 1
```
