# 51 Eight Queens  #20aug24

### Theory
Place 8 queens on a chess board so that none of them attack each other,
Queen can move any number of blocks in a row column and diagonally
```
Backtracking 
systematically search for a solution
build the solution one step at a time( keep trying to extend the next solution) 
if we hit a dead end ( if we cannot, undo the previous move and try again)
undo the last step 
try the next option (exhaustively search through all possibilities, systematically)
```

```
n queens in n x n
in a 2 x 2 grid, 2 queens are not possible
in a 3 x 3 grid, 3 queens are not possible

4 queens in 4 x 4 is possible,
this is possible upto 8 queens in 8 x 8
this is the limit as chess board is 8 x 8

> only one queen can be placed in a per row, column
> placing one queen per each row, marking the attack blocks
> in each row, placing the queen in the first available column
> when 8th queen cannot be placed, undo 7th queen (doesnt add other choice)
> undo 6th queen, no other choice opens
> undo 5th queen, try the next possible possition in the 5th row
> if doesnt work, trace back again
```
## Pseudocode 
```
representing the board
	n x n grid, number of rows and columns from 0 to n-1
	board[i][j] == 1 indicates queen at (i,j)
	board[i][j] == 0 indicates no queen

there can be only one queen per row ( there will be n number of 1)
	single list board of length n with entries 0 to n-1
	board[i] == j: queen in row i, column j, i.e (i,j)
		at i row, queen is at j column
```

```python
# Pseudocode of overall structure

def placequeen(i, board):  # trying row i, current state of the board
	for each c such that (i,c) is available:  # in column c, checking (i,c) availability
		place queen at (i,c) and update board  # if available place queen
		if i == n-1
			return(True)    # last queen has been placed
		else:
			extend_soln = placequeen(i+1, board)   # recursion with new row, new board
		# extend_soln records True or False based on if it succeeds or not
		
		if extend_soln:         
			return(True)     # This solution extends fully
		else:                # if False, will undo the move and backtrack
			undo this move and update board
	else:     # when for loop ends without returning True, there was no solution
		return (False)    # Row i failed
```

## Updating the board
```
A 2D representation with 0 and 1
A 1D representation gives column possition in each row to keep track of the queens

Need an efficient way to compute which squares are free to place the next queen.
	n x n attack grid
	> attack[i][j] == 1  if (i,j) can be attacked by a queen
	> attack[i][j] == 0 if (i,j) is currently available

Each [i][j] can be attacked by multiple queens,
while undoing a queen, which attack[i][j] should be reset to 0?
	queens are added row by row
	number the queens 0 to n-1
	record the earliest queen attcks in each square
	> attack[i][j] == k, if queen k first attacked (i,j)
	> attack[i][j] == -1 if (i,j) is free
	> when we remove queen k, we reset only those attack[i][j] == k to -1
	> all other squares are still attacked by earlier queens

attack requires n^2 space
	each update only requires only O(n) time
	only need to scan row, column, two diagonals
	
Can we improve our representation to use only O(n) space?
```

```
Numbering Diagonals

An individual square(i,j) is attacked by upto 4 queens
	queens on row i and column j
	one queen on each diagonal through (i,j)
	
In a decreasing diagonal: (left up to right down)
	(column - row) is invariant(constant)

In a increasing diagonal: 
	(column + row) is constant(nowhere that number will come)

a square(i,j) is attacked if
	> row i is attacked
	> column j is attacked
	> diagonal j-i is attacked
	> diagonal j+i is attacked

O(n) representation
	> row[i] == 1  if row is attacked by 0...N-1
	> col[i] == 1 if column i is attacked by 0...N-1
	> NEtoSE[i] == 1 if NW to SW diagonal i is attacked by,  -(N-1) to (N-1)
# (along decresing diagonal, for (column-row) the square will have numbers from 7 to -7 for a 8x8 grid)  [7-0, 6-1, .... 1-6, 0-7] )
	> SWtoNW[i] == 1 if SW to NE diagonal i is attacked by 0 to 2(N-1)
#(along increasing diagonal, for (column+row)), the squares will go from 0 to 14)

So now to check if a square (i,j) is under attack, we have to check if
	(row[i] == 1 or column[j] == 1 or (j-i)diagonal == 1 or (j+i)diagonal == 1)
if any of these are 1, then it is under attack, 

if all are 0, then it is free
	row[i] == column[j] == (j-i)diagonal == (j+i)diagonal == 0


# To add queen at (i,j)
	board[i] = j
	( row[i], column[j], (j-i)diagonal, (j+i)diagonal )= (1,1,1,1)

# To remove queen at (i,j)
	board[i] = -1
	( row[i], column[j], (j-i)diagonal, (j+i)diagonal )= (0,0,0,0)

# Implimentation detail on storing and passing values
	Main board as a nested dictionary
	> board['queen'][i] = j : Queen located at (i,j)
	> board['row'][i] = 1 : row i is attacked
	> board['col'][i] = 1 : column i is attacked
	> board['NWtoSE'][i] = 1 : NWtoSW diagonal i attacked
	> board['SWtoNE'][i] = 1 : SWtoNE diagonal i attacked
```

## First implementation from course (didn't work)
```python
def initialize(board,n):
	for key in ['queen', 'row', 'col', 'nwtose', 'swtone']:
		board[key] = {}
	for i in range(n):
		board['queen'][i] = -1
		board['row'][i] = 0
		board['col'][i] = 0
	for i in range( -(n-1), n):
		board['nwtose'] = 0       #[i] missing
	for i in range( 0, 2*(n-1)):  # 2*(n-1)+1
		board['swtone'] = 0       # [i] missing

def printboard(board):
	for row in sorted (board['queen'].keys()):       # lot missing
		print( (row, board['queen'][row], end=" " ))

def free(i,j,board):
	return(board['row'][i] == 0 and 
		   board['col'][j] == 0 and 
		   board['nwtose'][j-1] == 0 and 
		   board['swtone'][j+i] == 0)

def addqueen(i,j,board):
	board['queen'][i] = j
	board['row'][i] = 1
	board['col'][j] = 1
	board['nwtose'][j-i] = 1
	board['swtone'][j+i] = 1

def undoqueen(i,j,board):
	board['queen'][i] = -1
	board['row'][i] = 0
	board['col'][j] = 0
	board['nwtose'][j-i] = 0
	board['swtone'][j+i] = 0

def placequeen(i,board):
	n = len( board['queen'].keys() )    # way of finding n
	
	for j in range(n):
		if free(i,j,board):
			addqueen(i,j,board)
			if i == n-1:
				return(True)
			else:
				extendsoln = placequeen(i+1, board)
				if extendsoln:
					return(True)
				else:
					undoqueen(i,j,board)
	else:
		return(False)

board = {}
n = int(input("How many queens? "))
initialize(board, n)
if placequeen(0,board):
	printboard(board)
```

# Code that worked (from GPT)
```python
def initialize(board, n):
    for key in ['queen', 'row', 'col', 'nwtose', 'swtone']:
        board[key] = {}
    for i in range(n):
        board['queen'][i] = -1
        board['row'][i] = 0
        board['col'][i] = 0          # n colums, rows and queens
    for i in range(-(n-1), n):       # there are 14 different diagonals!
        board['nwtose'][i] = 0       # unique no for each is (j-i) (j+i)
    for i in range(0, 2*(n-1) + 1):
        board['swtone'][i] = 0    # no need to return board, dict is mutable so passsed

def placequeen(i, board):
    n = len(board['queen'])
    
    for j in range(n):              # in row i, iterate over colums j
        if free(i, j, board):       # Check if (i,j) is free
            addqueen(i, j, board)   # if free, add queen
            if i == n - 1:          # base case, last row queen placed
                return True         # otherwise increment row
            else:
                extendsoln = placequeen(i + 1, board)    # recursion with next row
                
                if extendsoln:                           # if queen is placed
                    return True
                else:   # for loop ended, no True, returned False, then undo last i
                    undoqueen(i, j, board)
    return False

def free(i, j, board):        # True if rows and colums are 0
    return (board['row'][i] == 0 and       # not checking queen, not necessary
            board['col'][j] == 0 and 
            board['nwtose'][j - i] == 0 and 
            board['swtone'][j + i] == 0)

def addqueen(i, j, board):
    board['queen'][i] = j       # i th row has j th queen 
    board['row'][i] = 1
    board['col'][j] = 1
    board['nwtose'][j - i] = 1
    board['swtone'][j + i] = 1

def undoqueen(i, j, board):
    board['queen'][i] = -1
    board['row'][i] = 0
    board['col'][j] = 0
    board['nwtose'][j - i] = 0
    board['swtone'][j + i] = 0

def printboard(board):
    n = len(board['queen'])
    board_matrix = [['.'] * n for _ in range(n)]    # makinh n x n matrix list, List of lists
    for i in range(n):
        j = board['queen'][i]      # the value is the j element
        if j != -1:
            board_matrix[i][j] = 'Q'  # i is there, j from list

    for row in board_matrix:
        print(' '.join(row))

board = {}
n = int(input("How many queens? "))
initialize(board, n)     # Board is ready

if placequeen(0, board):   # Passing first row and board
    printboard(board)      # If returns true, print
else:
    print("No solution exists.")
```

# Code for all solution
```python
def initialize(board, n):
    for key in ['queen', 'row', 'col', 'nwtose', 'swtone']:
        board[key] = {}
    for i in range(n):
        board['queen'][i] = -1
        board['row'][i] = 0
        board['col'][i] = 0
    for i in range(-(n-1), n):
        board['nwtose'][i] = 0
    for i in range(0, 2*(n-1) + 1):
        board['swtone'][i] = 0

def printboard(board):
    n = len(board['queen'])
    board_matrix = [['.'] * n for _ in range(n)]
    for i in range(n):
        j = board['queen'][i]
        if j != -1:
            board_matrix[i][j] = 'Q'
    return "\n".join(" ".join(row) for row in board_matrix)

def free(i, j, board):
    return (board['row'][i] == 0 and 
            board['col'][j] == 0 and 
            board['nwtose'][j - i] == 0 and 
            board['swtone'][j + i] == 0)

def addqueen(i, j, board):
    board['queen'][i] = j
    board['row'][i] = 1
    board['col'][j] = 1
    board['nwtose'][j - i] = 1
    board['swtone'][j + i] = 1

def undoqueen(i, j, board):
    board['queen'][i] = -1
    board['row'][i] = 0
    board['col'][j] = 0
    board['nwtose'][j - i] = 0
    board['swtone'][j + i] = 0

def placequeen(i, board, solutions):
    n = len(board['queen'])
    for j in range(n):
        if free(i, j, board):
            addqueen(i, j, board)
            if i == n - 1:
                # We've placed queens in all rows
                solutions.append(printboard(board))
            else:
                placequeen(i + 1, board, solutions)
            undoqueen(i, j, board)
    return solutions

board = {}
n = int(input("How many queens? "))
initialize(board, n)
solutions = []
placequeen(0, board, solutions)
if solutions:
    for solution in solutions:
        print("Solution:")
        print(solution)
        print()
else:
    print("No solution exists.")

```

# My implementation that actually worked !!! 
```python
def initialize(n,board):
    for key in ["q", "r", "c", "dd", "id"]:
        board[key] = {}
    for i in range(0,n):
        board["q"][i] = -1
        board["r"][i] = 0
        board["c"][i] = 0
    for i in range( -(n-1), n):
        board["dd"][i] = 0
    for i in range( 0, 2*(n-1)+1):
        board["id"][i] = 0
# there was no need of range for list of keys in ['q', 'r', . .]
# return is not needed for dict, return doesnt cause any issue
# id is increasing diagonal, dd is decreasing diagonal
# need some more practice in making dict in dict with keys

# Can remove all the Board from argument, as a dict need not be passed

def free(i,j,board):
    return(board["r"][i] == 0 and
        board["c"][j] == 0 and
        board["dd"][j-i] == 0 and
        board["id"][j+i] == 0 )
# while just returning True or false, just return would be enough
# some function all() passing a list might work, didnt try it

def addqueen(i,j,board):
    board["q"][i] = j
    board["r"][i] = 1
    board["c"][j] = 1
    board["dd"][j-i] = 1
    board["id"][j+i] = 1
# shouldnt make mistake while making keys and assigning values in j-i, j+i

def removequeen(i,j,board):
    board["q"][i] = -1
    board["r"][i] = 0
    board["c"][j] = 0
    board["dd"][j-i] = 0
    board["id"][j+i] = 0


def placequeen(i, board):
    n = len(board["q"])
    for j in range(0,n):
        if free(i,j,board):
            addqueen(i,j,board)
            if i == (n-1):
                return(True)
            else:
                nextrow = placequeen(i+1, board)
                if nextrow:
                    return True
                else:
                    removequeen(i,j,board)
    else:
        return False
# The logic was easy, building other def as i was going, but should first make a proper pseudocode detailing everything

def printboard(n,board):
    matrix = [["-"] *n for _ in range(n)]
    for i in range(n):
        j = board['q'][i]
        if j != -1:
            matrix[i][j] = 'Q'
    for row in matrix:
        print(row)
# this seemed more challenging than other things, making a new matrix, out of nested list because if just "_" is passed, then updatingg it to "Q" wont be possible as string is immutable in place. 
# total value of list[][] can be changed, not updating it so ["_"] works not "_"

board = {}
n = int(input("How many Queens?  "))
initialize(n,board)
placequeen(0,board)

for i in board:        # this just for fun
    print( i, board[i] )  

printboard(n, board)
```


# My Leetcode Submission (distinct solutions)
```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        board = {}
        solutions = []
        self.initialize(n, board)
        self.placequeen(0, board,solutions)
        return solutions
  
    def initialize(self, n, board):
        for key in ["q","c","r","dd","id"]:
            board[key] = {}
        for i in range(0, n):
            board["q"][i] = -1
            board["r"][i] = 0
            board["c"][i] = 0
        for i in range ( -(n-1), n):
            board["dd"][i] = 0
        for i in range ( 0, 2*(n-1)+1):
            board["id"][i]= 0
  
    def addqueen(self, i, j, board):        
        board["q"][i] = j
        board["r"][i] = 1
        board["c"][j] = 1
        board["dd"][j-i] = 1
        board["id"][j+i] = 1
  
    def placequeen(self, i, board, solutions):
        n = len(board["q"])
        if i == n:
            solutions.append(self.board_to_string(board))
            return
  
        for j in range(0,n):
            if self.freespace(i,j,board):
                self.addqueen(i,j,board)
                self.placequeen(i+1, board,solutions)
                self.removequeen(i,j,board)
  
    def freespace(self, i,j,board):
        return(board["r"][i] == 0 and
            board["c"][j] == 0 and
            board["dd"][j-i] == 0 and
            board["id"][j+i] == 0 )
  
    def removequeen(self, i,j,board):
        board["q"][i] = -1
        board["r"][i] = 0
        board["c"][j] = 0
        board["dd"][j-i] = 0
        board["id"][j+i] = 0
  
    def board_to_string(self, board):
        n = len(board["q"])
        matrix = [["."]*n for _ in range(0,n)]
  
        for i in range(0,n):
            j = board["q"][i]
            if j != -1:
                matrix[i][j] = "Q"
        return [ "".join(row) for row in matrix]
```

# Quickest solution on Leetcode
```python
from typing import List

class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        # Sets to keep track of columns and diagonals where queens are placed
        columns = set()
        posDiagonal = set()  # Positive slope diagonals (r + c)
        negDiagonal = set()  # Negative slope diagonals (r - c)
        
        # List to store all the valid solutions
        res = []
        
        # Initialize the board with empty cells
        board = [['.'] * n for _ in range(n)]
        
        def back(r):
            if r == n:  # If all queens are placed
                # Add the current board configuration to results
                res.append([''.join(row) for row in board])
                return
            
            for c in range(n):
                # Skip column if it is already occupied or the diagonals are attacked
                if c in columns or (r + c) in posDiagonal or (r - c) in negDiagonal:
                    continue
                
                # Place the queen
                columns.add(c)
                posDiagonal.add(r + c)
                negDiagonal.add(r - c)
                board[r][c] = 'Q'
                
                # Recur to place queens in the next row
                back(r + 1)
                
                # Remove the queen and backtrack
                columns.remove(c)
                posDiagonal.remove(r + c)
                negDiagonal.remove(r - c)
                board[r][c] = '.'
        
        # Start the backtracking from the first row
        back(0)
        
        return res
```

# GPT Explanation
let’s break down the `solveNQueens` method step by step to understand how it finds all solutions to the N-Queens problem. 
### Overview
The N-Queens problem requires placing `n` queens on an `n x n` chessboard such that no two queens threaten each other. This means no two queens can be in the same row, column, or diagonal.
### Detailed Breakdown
1. **Initialization**
   ```python
   columns = set()
   posDiagonal = set()  # Positive slope diagonals (r + c)
   negDiagonal = set()  # Negative slope diagonals (r - c)
   res = []
   board = [['.'] * n for _ in range(n)]
   ```

   - **`columns`**: Keeps track of the columns where queens are placed. If a column is in this set, it means it already contains a queen.
   - **`posDiagonal`**: Keeps track of diagonals with a positive slope. The diagonal is identified by the sum of the row and column indices (`r + c`).
   - **`negDiagonal`**: Keeps track of diagonals with a negative slope. The diagonal is identified by the difference between the row and column indices (`r - c`).
   - **`res`**: A list to store all valid solutions. Each solution is represented as a list of strings.
   - **`board`**: A 2D list representing the chessboard. Initially, it's filled with `'.'` to denote empty cells.

2. **Backtracking Function (`back`)**
   ```python
   def back(r):
       if r == n:
           res.append([''.join(row) for row in board])
           return
   ```
   - **Base Case**: When `r == n`, it means all rows are filled with queens. At this point, the current configuration of `board` is a valid solution, and it is added to `res`.
   - `[''.join(row) for row in board]` converts each row list (which contains `'Q'` or `'.'`) into a string and collects these rows into a list representing the board.

3. **Placing Queens**
   ```python
   for c in range(n):
       if c in columns or (r + c) in posDiagonal or (r - c) in negDiagonal:
           continue

       columns.add(c)
       posDiagonal.add(r + c)
       negDiagonal.add(r - c)
       board[r][c] = 'Q'
   ```
   - **Column and Diagonal Checks**: For each column `c`, the algorithm checks if placing a queen at position `(r, c)` is valid:
     - The column `c` should not be in `columns` (to avoid another queen in the same column).
     - The diagonal `r + c` should not be in `posDiagonal` (to avoid another queen on the same positive slope diagonal).
     - The diagonal `r - c` should not be in `negDiagonal` (to avoid another queen on the same negative slope diagonal).
   - If the position is valid, the queen is placed:
     - `columns.add(c)` marks the column as occupied.
     - `posDiagonal.add(r + c)` and `negDiagonal.add(r - c)` mark the diagonals as occupied.
     - `board[r][c] = 'Q'` places the queen on the board.

4. **Recursive Call**
   ```python
   back(r + 1)
   ```
   - After placing a queen, the function recurses to attempt to place queens in the next row (`r + 1`).

5. **Backtracking**
   ```python
   columns.remove(c)
   posDiagonal.remove(r + c)
   negDiagonal.remove(r - c)
   board[r][c] = '.'
   ```
   - After exploring all possibilities with the current queen placement, the algorithm backtracks by removing the queen and reverting the board to its previous state:
     - `columns.remove(c)` removes the column from the set.
     - `posDiagonal.remove(r + c)` and `negDiagonal.remove(r - c)` remove the diagonals from the sets.
     - `board[r][c] = '.'` clears the queen from the board.

6. **Starting Backtracking**
   ```python
   back(0)
   ```
   - The backtracking process starts from the first row (`r = 0`).

7. **Returning Results**
   ```python
   return res
   ```
   - Finally, the function returns the list of all valid solutions found.
### Summary
- **Initialization**: Sets up data structures to keep track of placed queens and the board state.
- **Backtracking Function**: Recursively places queens row by row, ensuring no conflicts with already placed queens.
- **Validation**: Each placement is checked for column and diagonal conflicts.
- **Backtracking**: After exploring all possibilities for a queen placement, it backtracks to try different configurations.
- **Result Collection**: Valid board configurations are collected and returned as the solution to the problem.

This approach efficiently finds all valid solutions to the N-Queens problem using backtracking.