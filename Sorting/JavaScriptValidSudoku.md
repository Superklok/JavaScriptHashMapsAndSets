# JavaScript Valid Sudoku

## Challenge:

Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated according to the following rules:
<br/>
Each row must contain the digits `1-9` without repetition.
<br/>
Each column must contain the digits `1-9` without repetition.
<br/>
Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.
<br/>

Note:
<br/>
A Sudoku board (partially filled) could be valid but is not necessarily solvable.
<br/>
Only the filled cells need to be validated according to the mentioned rules.

### 1<sup>st</sup> Example:

`Input: board =`
<br/>
`[["5","3",".",".","7",".",".",".","."]`
<br/>
`,["6",".",".","1","9","5",".",".","."]`
<br/>
`,[".","9","8",".",".",".",".","6","."]`
<br/>
`,["8",".",".",".","6",".",".",".","3"]`
<br/>
`,["4",".",".","8",".","3",".",".","1"]`
<br/>
`,["7",".",".",".","2",".",".",".","6"]`
<br/>
`,[".","6",".",".",".",".","2","8","."]`
<br/>
`,[".",".",".","4","1","9",".",".","5"]`
<br/>
`,[".",".",".",".","8",".",".","7","9"]]`
<br/>
`Output: true`

### 2<sup>nd</sup> Example:

`Input: board =`
<br/>
`[["8","3",".",".","7",".",".",".","."]`
<br/>
`,["6",".",".","1","9","5",".",".","."]`
<br/>
`,[".","9","8",".",".",".",".","6","."]`
<br/>
`,["8",".",".",".","6",".",".",".","3"]`
<br/>
`,["4",".",".","8",".","3",".",".","1"]`
<br/>
`,["7",".",".",".","2",".",".",".","6"]`
<br/>
`,[".","6",".",".",".",".","2","8","."]`
<br/>
`,[".",".",".","4","1","9",".",".","5"]`
<br/>
`,[".",".",".",".","8",".",".","7","9"]]`
<br/>
`Output: false`
<br/>
`Explanation: Same as Example 1, except with the 5 in the top left corner being modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.`

### Constraints:

`board.length == 9`
<br/>
`board[i].length == 9`
<br/>
`board[i][j]` is a digit `1-9` or `'.'`.

## Solution:

`const isValidSudoku = (board) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const map = {};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let i = 0; i < 9; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let j = 0; j < 9; j++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let num = board[i][j],`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`x   = Math.floor(i / 3),`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`y   = Math.floor(j / 3),`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`err = (map['r' + i + num] ||`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`map['c' + j + num] ||`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`map['b' + x + y + num]);`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(board[i][j] === '.') {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`continue;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>      
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(err) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return false;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`map['r' + i + num] = 1;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`map['c' + j + num] = 1;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`map['b' + x + y + num] = 1;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return true;`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've defined a function called `isValidSudoku` that takes a Sudoku board as input and checks if it is a valid Sudoku solution. It returns `true` if the board is valid and `false` otherwise.
<br/>

Inside the function, an empty object called `map` is initialized. This object will be used to keep track of the numbers that have already appeared in each row, column, and 3x3 box of the Sudoku board.
<br/>

Two nested loops are used to iterate over each cell of the Sudoku board. The outer loop iterates over the rows (`i`) and the inner loop iterates over the columns (`j`).
<br/>

Inside the loop, several variables are defined: `num` represents the number in the current cell of the board, `x` represents the index of the 3x3 box in the row, `y` represents the index of the 3x3 box in the column, and `err` is a flag indicating whether there is an error (duplicate number) in the current row, column, or 3x3 box.
<br/>

The function checks if the number in the current cell is a dot ('.'). If it is, it means the cell is empty, and the rest of the code for this cell is skipped using the `continue` statement.
<br/>

If there is an error (`err` is truthy), it means the current number has already appeared in the same row, column, or 3x3 box. In this case, the function returns `false` to indicate that the Sudoku board is not valid.
<br/>

If there is no error, the `map` object is updated by setting the corresponding keys to `1`. These keys are constructed using the row index (`r`), column index (`c`), and 3x3 box indices (`b`) concatenated with the number (`num`). This marks the number as seen in the respective row, column, and 3x3 box.
<br/>

After the loops have finished iterating over all the cells, the function returns `true` to indicate that the Sudoku board is valid.
<br/>

In summary, the `isValidSudoku` function checks if a given Sudoku board is valid by ensuring that no number is repeated in the same row, column, or 3x3 box. It uses an object (`map`) to keep track of the numbers that have already appeared in each row, column, and box.
<br/>
<br/>