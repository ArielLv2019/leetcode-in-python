- [Merge Sort](#merge-sort)
- [Binary Search](#binary-search)


# Merge Sort

Time Complexity: O(m+n)

```python
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        nums = nums1 + nums2
        nums = sorted(nums)
        length = len(nums)
        return nums[length//2] if length % 2 else (nums[length//2]+nums[(length//2)-1])/2
```

# Binary Search

Time Complexity: O(log(m+n))

```python
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        def kth(a, b, k):
            if not a:
                return b[k]
            if not b:
                return a[k]

            aMid, bMid = len(a) // 2, len(b) // 2

            # evict left half
            if aMid + bMid < k:
                if a[aMid] > b[bMid]:
                    return kth(a, b[bMid + 1:], k - bMid - 1)
                else:
                    return kth(a[aMid + 1:], b, k - aMid - 1)
            else: # evict right half
                if a[aMid] > b[bMid]:
                    return kth(a[:aMid], b, k)
                else:
                    return kth(a, b[:bMid], k)
                
        l = len(nums1) + len(nums2)
        if l % 2 == 1:
            return kth(nums1, nums2, l // 2)
        else:
            return (kth(nums1, nums2, l // 2) + kth(nums1, nums2, l // 2 - 1)) / 2
```
