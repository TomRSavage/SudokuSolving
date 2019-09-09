# SudokuSolving
A framework and visualisation tool for solving sudokus using stochastic optimisation

<p align="center">
 <img src="https://github.com/TomRSavage/SudokuSolving/blob/master/SodukoSolve.gif" width="700">
</p>

## Function Use 

The code takes an unsolved sudoku in the form if an array of length 81, working from left to right, top to bottom. Empty values are represented by 0's. 

For use with other stochastic optimisation algorithms, the function plot_util takes an unsolved sudoku vector, the vector of input values, the cost function value, and the iteration number. Then saves a .png with the plot.

```
unsolved=np.array([3,9,6,0,8,0,7,1,5,\
0,0,7,9,6,1,0,0,3,\
8,4,1,0,3,0,2,0,0,\
6,3,0,1,0,0,5,2,0,\
1,0,0,7,2,5,3,9,0,\
0,5,2,6,9,3,8,0,1,\
4,0,8,3,7,6,0,0,2,\
2,0,5,8,0,9,0,3,4,\
9,6,3,0,0,2,0,7,8])

.
.
.


solved=evolution(cost_function,100,100,0.8,0.05,unsolved)
```
Returns
<p align="center">
 <img src="https://github.com/TomRSavage/SudokuSolving/blob/master/SodukoSolve.gif" width="400">
</p>
