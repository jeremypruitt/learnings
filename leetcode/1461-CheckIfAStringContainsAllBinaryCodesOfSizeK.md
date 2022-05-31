# 1461 - Check If a String Contains All Binary Codes of Size K

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/check-if-a-string-contains-all-binary-codes-of-size-k/
| Language | Python 3
| Runtime | 677 ms, faster than 28.32% of Python3 online submissions for Check If a String Contains All Binary Codes of Size K
| Memory Usage | 27.2 MB, less than 51.77% of Python3 online submissions for Check If a String Contains All Binary Codes of Size K
| Datastructures | set, queue
| Algorithms | bit manipulation, iterate

### Procedure

1. TBD...

### Code

#### Option 1

```python
class Solution:
    def hasAllCodes(self, s: str, k: int) -> bool:
        codes = set()
        queue = []

        # Loop over each character in the string and add to queue
        for char in s:
            queue.append(char)

            # Add joined queue to list of codes and pop from queue
            if len(queue) == k:
                codes.add(''.join(queue))
                queue.pop(0)

        # True if number of codes is 2 to power of k
        return len(codes) == 1 << k
```

#### Option 2

```python
class Solution:
    def hasAllCodes(self, s: str, k: int) -> bool:
        codes = set()

        # Loop over range from 1 to beginning of the final slice
        for i in range(len(s) - k+1):
            # Add the current slice of size k
            codes.add(s[i:i+k])

        # True if number of codes is 2 to power of k
        return len(codes) == 2 ** k
```

#### Option 3: One-Liner

```python
class Solution:
    def hasAllCodes(self, s: str, k: int) -> bool:
        return len({
            s[i:i + k] for i in range(len(s) - k + 1)
        }) == 2 ** k
```
