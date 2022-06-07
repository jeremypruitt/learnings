# 88 - Merge Sorted Array

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/merge-sorted-array/
| Language | Python 3
| Runtime | 75 ms, faster than 10.42% of Python3 online submissions for Merge Sorted Array
| Memory Usage | 13.8 MB, less than 85.45% of Python3 online submissions for Merge Sorted Array
| Datastructures | List[int]
| Algorithms | slice

### Procedure

1. TBD...

### Code

#### Option 1: Python Built-Ins

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        nums1[m:] = nums2
        nums1.sort()
```

#### Option 2

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        while n:
            if m and nums1[m-1] >= nums2[n-1]:
                nums1[m+n-1] = nums1[m-1]
                m -= 1
            else:
                nums1[m+n-1] = nums2[n-1]
                n -= 1
```
