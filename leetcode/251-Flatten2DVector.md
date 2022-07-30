# 251 - Flatten 2D Vector

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/flatten-2d-vector/
| Language | Python 3
| Runtime | 146 ms, faster than 28.49% of Python3 online submissions for Flatten 2D Vector
| Memory Usage | 19.3 MB, less than 52.37% of Python3 online submissions for Flatten 2D Vector
| Datastructures | List[List[int]]
| Algorithms | Flatten in Constructor
| Complexity | Time: O(N+V) Memory: O(N) (N=number of ints in vector, V=number of inner vectors)

### Notes

Here's a [Stackoverflow discussion](https://stackoverflow.com/q/2776829) that's helpful for understanding generators:

> Generators are a simple and powerful tool for creating iterators.
> They are written like regular functions but use the yield
> statement whenever they want to return data. Each time next() is
> called on it, the generator resumes where it left off (it remembers
> all the data values and which statement was last executed).

*Also note that a two-pointer solution would be more space efficient.*

### Procedure

1. ...

### Code

```python
class Vector2D:

    def __init__(self, vec: List[List[int]]):
        #def generator():
        #    for row in vec:
        #        for col in row: yield col
        #self.gen = generator()
        self.gen = (col for row in vec for col in row)
        self.next_val = next(self.gen, None)

    def next(self) -> int:
        result = self.next_val
        self.next_val = next(self.gen, None)
        return result

    def hasNext(self) -> bool:
        return self.next_val is not None    

# Your Vector2D object will be instantiated and called as such:
# obj = Vector2D(vec)
# param_1 = obj.next()
# param_2 = obj.hasNext()
```
