- [Backtracking](#Backtracking)


# Backtracking

```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        ans = []
        
        def bt(start, remaining, prefix):
            if remaining == 0:
                if prefix not in ans:
                    ans.append(prefix)
                return
            elif remaining < 0:
                return
                
            for idx in range(start, len(candidates)):
                bt(idx+1, remaining - candidates[idx], prefix + [candidates[idx]])
                
            
        candidates.sort()
        bt(0, target, [])
        return ans
```
