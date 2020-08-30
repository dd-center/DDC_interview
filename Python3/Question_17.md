# Sudoku Solver

```
Write a program to solve a Sudoku puzzle by filling the empty cells.
```
🎉 Answer
```python3
class Solution:
    find_target_answer = False
    def solveSudoku(self, board_real: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        def remaining_choices(row_values, col_values, sub_box_values):
            'remove all the impossible values'
            total_list = ['1', '2', '3', '4', '5', '6', '7', '8', '9']
            removing_values = set(row_values + col_values + sub_box_values)
            for remove_target in removing_values:
                total_list.remove(remove_target)
            return total_list    

        def select_row_col_sub_box(board, row_index, col_index):
            'select row, col'
            row_values = []
            for i in range(9):
                if board[row_index][i] != '.':
                    row_values.append(board[row_index][i])

            col_values = []
            for i in range(9):
                if board[i][col_index] != '.':
                    col_values.append(board[i][col_index])

            'deal with sub_box'
            sub_box_values = []
            for row in range(3 * (row_index//3), 3 * (1 + row_index//3)):
                for col in range(3 * (col_index//3), 3 * (1 + col_index//3)):
                    if board[row][col] != '.':
                        sub_box_values.append(board[row][col])

            return row_values, col_values, sub_box_values

        def dfs(board, row_index, col_index):
            if self.find_target_answer:
                return
            if row_index == 9:
                self.find_target_answer = True              
                return                

            if board[row_index][col_index] == '.':
                row_values, col_values, sub_box_values = select_row_col_sub_box(board, row_index, col_index)
                candidate_list = remaining_choices(row_values, col_values, sub_box_values)
                if not candidate_list:
                    return                
                for candidate in candidate_list:
                    if not self.find_target_answer:
                        board[row_index][col_index] = candidate
                    'try to iterate over the board'
                    if col_index >= 8:
                        dfs(board, row_index + 1, 0)
                    else:
                        dfs(board, row_index, col_index + 1)
                    if not self.find_target_answer:
                        board[row_index][col_index] = '.'    
            else:
                'try to iterate over the board'
                if col_index >= 8:
                    dfs(board, row_index + 1, 0)
                else:
                    dfs(board, row_index, col_index + 1)        

        dfs(board_real, 0, 0)
```
