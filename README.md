# SudokuSolving
A framework and visualisation tool for solving sudokus using stochastic optimisation

## Inspiration

I was recently doing a sudoku puzzle on the train to fill some time, whilst also half updating one of my GitHub repositories regarding stochastic optimisation. I had the realisation that (like most problems) if I'm clever with how I produce a cost function, I could use optimisation to do all the work for me! 

## Creating a Cost Function 

Having decided that I was going to now solve this high-dimensional, highly non-linear, integer based optimisation problem, I started to work on the creation of my cost function. It needed to obviously be the lowest for a completely solved sudoku and provide some sort of insight into which 'solutions' are better than others (I say 'solutions' because there is obviously only one solution per sudoku, however we'll hopefully be producing a series of 'less wrong' solutions that converge towards the answer). 

I represent the initial empty suduko as an array with length 81, empty squares are represented with zeros. Our cost function takes an input array of size 81-n, where n is the number squares containing values. 

First things first we iterate through the empty sudoku, and if a square contains a 0 (is empty), we fill it with the first input value, then we continue through the empty sudoku until we find the next empty square, and fill it with the next input value. We repeat until we have a completed sudoku. 

Now with this completed array of length 81 we want to gain an insight into how close to the actual solution we are. Luckily Sudoku hinges on some fundamental rules which tell us exactly that. 

Simply, no number can appear more than once in each collumn, row, or 3x3 grid (9 of which make up the complete 9x9 grid). 
Now we first could say ok, well why don't we just add a penalty for every row, collumn, or 3x3 grid that doesn't add up to 45. Whilst this would produce no penalty for the actual solution, there is no ability for the function to penalise the same numbers in the same row, collumn or grid. Quite obviously there is more than one way of summing 9 numbers to make 45. 

A smarter solution would be to add a penalty for every number that appears more than once in each row, collumn or grid. So this is what is implemented here. We iterate over each row, then each collumn and finally each grid, transforming the 1x9 collumn vector and the 3x3 grid vector into a numpy array of length 9. We then use the python function 'set(x)' to produce an array of all the unique numbers in this 9 dimensional array, and add a penalty 9-(set(x)) for each row, collumn and grid. 

We now have a function that takes an input array and an empty sudoku, and returns the number of times a number is repeated in each row, collumn and grid. This is what we will optimise in order to find a final solution.

