- [Backtracking](#backtracking)


# Backtracking

```python
class Solution:
    """
    @param s: the given string
    @return: all the palindromic permutations (without duplicates) of it
    """
    def generatePalindromes(self, s):
        # write your code here
        from collections import defaultdict
        counter = defaultdict(int)

        def canPermutePalindrome(s):
            count = 0
            for ch in s:
                counter[ch] += 1
                if counter[ch] % 2 == 0:
                    count -= 1
                else:
                    count += 1

            return count <= 1

        if not canPermutePalindrome(s):
            return []

        pivot = None
        cand = []
        for k, v in counter.items():
            if v % 2 == 1:
                pivot = k

            cand.extend(k*(v//2))

        ans = []
        def permute(s, start, pvt):
            if start == len(s):
                item = '%s%s%s' % (''.join(s), pvt if pvt else '', ''.join(s[::-1]))
                ans.append(item)
                return

            for i in range(start, len(s)):
                if s[i] != s[start] or i == start:
                    s[i], s[start] = s[start], s[i]
                    permute(s, start+1, pvt)
                    s[i], s[start] = s[start], s[i]
        permute(cand, 0, pivot)
        return ans
```
