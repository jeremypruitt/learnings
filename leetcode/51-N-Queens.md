# 51 - N-Queens

### Details

| Key | Value |
| --- | ----- |
| Link | https://leetcode.com/problems/n-queens/
| Language | Python 3
| Runtime | 681 ms, faster than 5.01% of Python3 online submissions for N-Queens
| Memory Usage | 14.3 MB, less than 84.07% of Python3 online submissions for N-Queens
| Datastructures | List[List[str]]
| Algorithms | DFS/Backtracking

### Procedure

1. TBD...

### Code

```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        def dfs(board, row, valid_positions):
            if row == len(board):
                final_position = ["".join(row) for row in board]
                valid_positions.append(final_position)
                return
            
            for col in range(n):
                # Not a valid space
                if board[row][col] is not None:
                    continue
                    
                # Create new board with Q in current square
                new_board = deepcopy(board)
                new_board[row][col] = "Q"
                
                # Mark other squares in current row invalid
                for col_in_current_row in range(n):
                    if new_board[row][col_in_current_row] is None:
                        new_board[row][col_in_current_row] = "."
                
                # Above current row, all squares were marked Q or invalid.
                # Mark invalid squares below current row
                for i in range(row+1, n):
                    # Mark col going down as invalid
                    new_board[i][col] = "."
                    
                    # Mark rightward diag going down as invalid
                    if col+i-row < n:
                        new_board[i][col+i-row] = "."
                    
                    # Mark rightward diag going down as invalid
                    if col+row-i >= 0:
                        new_board[i][col+row-i] = "."
                
                # Search for square to place Q on next row
                dfs(new_board, row+1, valid_positions)
        
        empty_board = [[None] * n for _ in range(n)]
        first_row = 0
        valid_positions = []
        
        dfs(empty_board, first_row, valid_positions)
        
        return valid_positions
```
