# 1. Introduction:-

This project presents the implementation of a Sudoku solver using the framework of Constraint Satisfaction Problems (CSP). In this formulation, each cell in the Sudoku grid is treated as a variable with a domain of possible values from 1 to 9. The constraints ensure that no value is repeated within any row, column, or 3×3 subgrid.
The solution approach combines multiple CSP techniques, including Arc Consistency (AC-3), Backtracking Search, Forward Checking, and the Minimum Remaining Values (MRV) heuristic, to efficiently solve Sudoku puzzles of varying difficulty levels.
## Algorithms Used
AC-3 (Arc Consistency)
Backtracking Search
Forward Checking
MRV Heuristic

# 2.Problem Representation

# 2.1 Sudoku Grid
The Sudoku puzzle is represented as a 9×9 grid. Each cell contains a digit from 1 to 9 or 0, where 0 indicates an empty cell.
# 2.2  Variables and Domains
Each cell in the grid is treated as a variable. The domain of each variable is defined as follows:
•	If the cell is pre-filled, its domain contains only that value.
•	If the cell is empty, its domain initially contains all possible values {1, 2, ..., 9}.
## 3. Methodology

# 3.1 Domain Construction
The domains for all variables are initialized based on the input grid. Pre-filled cells are assigned a singleton domain, while empty cells are assigned the full domain of possible values.
# 3.2 Constraint Definition
Constraints are defined such that:
•	No two variables in the same row can have the same value.
•	No two variables in the same column can have the same value.
•	No two variables in the same 3×3 subgrid can have the same value.
Each variable maintains a set of neighboring variables (peers) that share these constraints.
## 4. Arc Consistency (AC-3)

The AC-3 algorithm is applied to enforce arc consistency before initiating the search process. It systematically removes values from domains that violate constraints with neighboring variables.
An arc (Xi, Xj) is considered consistent if, for every value in the domain of Xi, there exists at least one compatible value in the domain of Xj. In the context of Sudoku, compatibility means that the values are not equal.
If any domain becomes empty during this process, the puzzle is deemed unsolvable.
## 5. Backtracking Search

# 5.1 Variable Selection (MRV)
The Minimum Remaining Values (MRV) heuristic is used to select the next variable to assign. This heuristic chooses the variable with the smallest domain, thereby reducing the branching factor and improving efficiency.
# 5.2 Forward Checking
After assigning a value to a variable, forward checking is performed. This step removes the assigned value from the domains of all unassigned neighboring variables. If any domain becomes empty as a result, the algorithm backtracks.
# 5.3 Recursive Backtracking
The backtracking algorithm operates recursively as follows:
1.	If all variables are assigned, a solution has been found.
2.	Select an unassigned variable using MRV.
3.	Iterate through its domain values.
4.	Assign a value and apply forward checking.
5.	Recursively attempt to solve the reduced problem.
6.	If a failure occurs, undo the assignment and domain changes, and try the next value.
## 6. Performance Metrics
Two performance metrics are used to evaluate the efficiency of the solver:
•	Backtrack Calls: The total number of recursive calls made during the search process.
•	Backtrack Failures: The number of times the algorithm encounters a dead-end and must backtrack.
These metrics provide insight into the computational effort required to solve puzzles of different difficulty levels.
## Features
Solves Easy → Evil puzzles
Efficient constraint propagation
Performance metrics included
#  Author

Muhammad Saad
