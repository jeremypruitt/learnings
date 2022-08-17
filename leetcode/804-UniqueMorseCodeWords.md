# 804 - Unique Morse Code Words

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/unique-morse-code-words/
| Language | Python 3
| Runtime | 34 ms, faster than 96.53% of Python3 online submissions for Unique Morse Code Words
| Memory Usage | 13.9 MB, less than 75.48% of Python3 online submissions for Unique Morse Code Words
| Datastructures | List[str]
| Algorithms | Iterate & Count
| Complexity | Time: O(NK) Memory: O(N) (N=number of words, K=average length of words)

### Procedure

1. ...

### Code

```python
class Solution:
    def uniqueMorseRepresentations(self, words: List[str]) -> int:
        morse = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
        transformations = set()
        number_of_different_transformations = 0
        
        for word in words:
            transformation = ""
            for char in word:
                position_in_alphabet = ord(char) - 97
                transformation += morse[position_in_alphabet]
                
            if transformation not in transformations:
                transformations.add(transformation)
                number_of_different_transformations += 1
        
        return number_of_different_transformations
```
