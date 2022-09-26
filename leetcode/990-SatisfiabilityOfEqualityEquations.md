# 990 - Satisfiability of Equality Equations

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/satisfiability-of-equality-equations/submissions/
| Language | Python 3
| Runtime | 47 ms, faster than 94.56% of Python3 online submissions for Satisfiability of Equality Equations
| Memory Usage | 14.2 MB, less than 34.67% of Python3 online submissions for Satisfiability of Equality Equations
| Datastructures | List[str], Dict
| Algorithms | Union Find
| Complexity | Time: O(N) Memory: O(N)

### Procedure

1. ...

### Code

```python
class Solution:
    def equationsPossible(self, equations: List[str]) -> bool:
        parent, diff = {}, []

        def find(x):
            if x not in parent: return x
            return find(parent[x])

        for equation in equations:
            a, b = equation[0], equation[3]

            if equation[1]== "=":
                x, y = find(a), find(b)
                if x != y: parent[y] = x
            else:    
                diff.append((a,b))

        return all(find(a)!=find(b) for a, b in diff)
```
