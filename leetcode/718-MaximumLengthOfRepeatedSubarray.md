# 718 - Maximum Length of Repeated Subarray

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/maximum-length-of-repeated-subarray/
| Language | Python 3
| Runtime | 6476 ms, faster than 41.75% of Python3 online submissions for Maximum Length of Repeated Subarray
| Memory Usage | 14.1 MB, less than 88.72% of Python3 online submissions for Maximum Length of Repeated Subarray
| Datastructures | DP Table
| Algorithms | DP
| Complexity | Time: O(NM) Memory: O(NM)

### Procedure

1. ...

### Code

#### Option 1

```python
len_nums1, len_nums2 = len(nums1), len(nums2)
        max_len, prev = 0, [0] * (len(nums2)+1)

        for i_nums1 in range(len_nums1):
            curr = [0] * (len_nums2 + 1)  
          
            for i_nums2 in range(len_nums2):
                if nums1[i_nums1] == nums2[i_nums2]: 
                    curr[i_nums2+1] = prev[i_nums2] + 1
                    max_len = max(max_len, curr[i_nums2+1])
                    
            prev = curr
            
        return max_len
```

#### Option 2

```python
len_nums1, len_nums2 = len(nums1), len(nums2)
        len_nums1, len_nums2 = len(nums1), len(nums2)
        
        dp = [[0] * (len_nums2 + 1) for _ in range(len_nums1 + 1)]
        
        for i_nums1 in range(len_nums1):
            for i_nums2 in range(len_nums2):
                if nums1[i_nums1] == nums2[i_nums2]:
                    dp[i_nums1][i_nums2] = dp[i_nums1-1][i_nums2-1] + 1
        
        return max(max(row) for row in dp)
```
