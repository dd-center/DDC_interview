# Unique Paths III
```python3
On a 2-dimensional grid, there are 4 types of squares:

1 represents the starting square.  There is exactly one starting square.
2 represents the ending square.  There is exactly one ending square.
0 represents empty squares we can walk over.
-1 represents obstacles that we cannot walk over.
Return the number of 4-directional walks from the starting square to the ending square, 
that walk over every non-obstacle square exactly once.

 

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/unique-paths-iii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```
🎉 Answer
```python3
class Solution:
    total_res = 0
    def uniquePathsIII(self, grid: List[List[int]]) -> int:
        'first, figure out the squares you need to walk over..'
        seq_counter = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] in [0, 1]:
                    seq_counter += 1
        
        def dfs(grid, seq_length, row, col):
            # print(f"{grid}, seq: {seq_length}, [{row}, {col}]")
            'make sure we are inside the grid'
            if row < 0 or row >= len(grid) or col < 0 or col >= len(grid[0]):
                return

            if grid[row][col] == 2:
                if seq_length == seq_counter:
                    'all necessary squares have been iterated, time to stop'
                    self.total_res += 1
                return

            if grid[row][col] == -1:
                return

            'go to four directions...'
            tmp = grid[row][col]   

            grid[row][col] = -1
            dfs(grid, seq_length + 1, row - 1, col)
            dfs(grid, seq_length + 1, row, col - 1)
            dfs(grid, seq_length + 1, row + 1, col)
            dfs(grid, seq_length + 1, row, col + 1)
            grid[row][col] = tmp 

        start_row, start_col = 0, 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == 1:
                    start_row, start_col = i, j
                    break

        dfs(grid, 0, start_row, start_col)
        return self.total_res        
```
